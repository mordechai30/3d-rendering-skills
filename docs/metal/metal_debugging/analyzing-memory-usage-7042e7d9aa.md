Source: [https://developer.apple.com/documentation/xcode/analyzing-memory-usage](<https://developer.apple.com/documentation/xcode/analyzing-memory-usage>)

<a id="analyzing-memory-usage"></a>

# Analyzing memory usage

Manage your Metal app’s memory usage by inspecting its resources.

<a id="overview"></a>

## Overview

The Memory viewer provides comprehensive information about your app’s memory usage in Metal.
The Memory viewer’s top section presents a breakdown of memory by categories, and the bottom section displays a table of resources.
In the table, you can inspect resources for their memory size, configuration, and other characteristics.

![A screenshot of the Memory viewer showing bar graphs in the top section that summarize the resource memory use, and a resources table in the bottom section.](<analyzing-memory-usage/fefbba4be3bb294e5050313e.png>)

Metal apps create many resources, and those resources consume a lot of memory.
For example, to render an animated character using a physically based renderer, you might need buffers to hold vertex and animation data, and multiple textures to provide material attributes.
When you scale these requirements to multiple characters and larger scenes, your app’s memory footprint grows significantly.

Additionally, when you create Metal resources, specifying their configuration precisely has a substantial effect on performance.
The Metal debugger analyzes the configuration you provide and uses it to create the underlying GPU representation of a resource.
For example, if you create a resource with a private storage mode, Metal can optimize the resource for GPU access, and doesn’t need to store data in a location or format directly accessible from the CPU.

<a id="examine-the-bar-graphs"></a>

### Examine the bar graphs

The categories in the top section of the Memory viewer organize memory usage data and provide memory totals based on the following criteria:

- Volatility:
  This category lists *volatile* and *nonvolatile* resources.
  Nonvolatile memory total is a good indicator of your app’s tracked memory usage for Metal.
  When you mark a resource as volatile, you give Metal permission to dispose of its contents when memory is scarce.
  The operating system doesn’t count volatile memory in your app’s total memory footprint.
  For example, in iOS, a lower footprint reduces the risk that you exceed the jetsam limit and have the operating system terminate your app.
  If you think that you might use a resource in the future that you’re not currently using, mark it as volatile rather than simply releasing it.
  That way, you only need to recreate the resource’s contents if Metal discards them.
  For more information, see <doc://com.apple.documentation/documentation/Metal/MTLResource/setPurgeableState(_:)>.
- Type:
  This category lists resources by type — textures, buffers, and so on.
  Check this category to determine whether your app is using any particular kind of resource more than others.
- Storage mode:
  This category lists resources by the modes that you define in <doc://com.apple.documentation/documentation/Metal/MTLStorageMode>.
  Check this category to determine whether an excessive number of resources are marked as <doc://com.apple.documentation/documentation/Metal/MTLStorageMode/shared> or <doc://com.apple.documentation/documentation/Metal/MTLStorageMode/managed>.
- Use:
  This category tracks whether commands accessed resources in the captured frame.
  Examine this category for a large total of unused resources, which might indicate that you need to release some resources or mark them as volatile.

Each bar graph consists of segments representing the largest resources that it tracks.
The final segment of each bar graph shows an aggregate total for its smaller resources.
Move your pointer over a segment to view a popover with the name of the resource, its size, and other information.
Click a segment to get more information about that specific resource.

![A screenshot of the Memory viewer’s bar graphs highlighting only texture resources. The texture that consumes the most memory is selected.](<analyzing-memory-usage/a49a2c5317eae2cc8c938573.png>)

<a id="inspect-the-resources-table"></a>

### Inspect the resources table

To improve how your app creates and manages resources, you need data about how it uses them.
The Memory viewer provides information about the resources that are live in your Metal app during a capture.

![A screenshot of the Memory viewer’s resources table.](<analyzing-memory-usage/d7eb0fb19d339c436c75797a.png>)

The resources table provides the following information for all resource types:

| Column | Property | Description |
| --- | --- | --- |
| Label | <doc://com.apple.documentation/documentation/Metal/MTLResource/label> | The label you add when creating the resource. Use this information to identify specific resources in your app. To learn how to name your resources, see <doc://com.apple.Xcode/documentation/Xcode/Naming-resources-and-commands>. |
| Insights |  | Possible problems or optimizations that might improve memory or resource usage. |
| Type |  | The type of resource. For a texture, this information includes the texture’s subtype. For a heap, it includes the heap’s subtype. |
| Allocated Size | <doc://com.apple.documentation/documentation/Metal/MTLResource/allocatedSize> | The allocated memory size for the resource. |
| Storage Mode | <doc://com.apple.documentation/documentation/Metal/MTLResource/resourceOptions> or <doc://com.apple.documentation/documentation/Metal/MTLResource/storageMode> | The storage mode you choose when creating the resource. |
| Purgeable State |  | The volatility of the resource. When you mark a resource as volatile, the system can purge it when free memory is low. The operating system doesn’t include volatile resources in the system memory total for your app. |
| Aliasable | <doc://com.apple.documentation/documentation/Metal/MTLResource/isAliasable()> | An indication of whether the resource shares its associated memory with another resource on the same heap. |
| CPU Access |  | An indication of whether your app has accessed the resource from the CPU. |
| Time Since Last Bound |  | The amount of time since last binding the resource to a Metal command encoder. If you’ve never bound the resource or haven’t bound it for a long time, you can probably release this resource or mark it as volatile. |

For textures, you can add the following columns:

| Column | Property | Description |
| --- | --- | --- |
| Pixel Format | <doc://com.apple.documentation/documentation/Metal/MTLTexture/pixelFormat> | The Metal pixel format you choose when creating the texture. |
| Width | <doc://com.apple.documentation/documentation/Metal/MTLTexture/width> | The width, in pixels, of the texture’s base mipmap. |
| Height | <doc://com.apple.documentation/documentation/Metal/MTLTexture/height> | The height, in pixels, of the texture’s base mipmap. |
| Depth | <doc://com.apple.documentation/documentation/Metal/MTLTexture/depth> | The depth, in pixels, of the texture’s base mipmap. |
| Array Length | <doc://com.apple.documentation/documentation/Metal/MTLTexture/arrayLength> | The number of slices in the texture array. |
| Mipmaps | <doc://com.apple.documentation/documentation/Metal/MTLTexture/mipmapLevelCount> | The number of mipmap levels in the texture. |
| Samples | <doc://com.apple.documentation/documentation/Metal/MTLTexture/sampleCount> | The number of samples in each pixel. |
| Usage | <doc://com.apple.documentation/documentation/Metal/MTLTexture/usage> | Indicates the actions a shader or app can perform on the texture. The more restricted the list, the more optimizations Metal can apply to the texture. |
| Lossless Compression |  | Indicates whether the texture supports lossless compression. |

For buffers, you can add the following column:

| Column | Property | Description |
| --- | --- | --- |
| Length | <doc://com.apple.documentation/documentation/Metal/MTLBuffer/length> | The logical length, in bytes, of the buffer. Compare this value to the allocated size. To make memory available to the GPU, Metal sometimes needs to allocate more memory than you request. If you see many small buffers, consolidate those that the system uses together into a single buffer, or allocate the buffers on a heap. These alternative allocation strategies save memory and require less work to track dependencies between commands accessing those resources. |

For heaps, you can add the following columns:

| Column | Property | Description |
| --- | --- | --- |
| Size | <doc://com.apple.documentation/documentation/Metal/MTLHeap/size> | The logical size, in bytes, of the heap. |
| Used Size | <doc://com.apple.documentation/documentation/Metal/MTLHeap/usedSize> | The number of bytes the heap allocates for other resources. |
| Hazard Tracking Mode | <doc://com.apple.documentation/documentation/Metal/MTLHeap/resourceOptions> or <doc://com.apple.documentation/documentation/Metal/MTLHeap/hazardTrackingMode> | The hazard tracking mode of the allocated resources on the heap. |

For indirect command buffers, you can add the following column:

| Column | Property | Description |
| --- | --- | --- |
| Size | <doc://com.apple.documentation/documentation/Metal/MTLIndirectCommandBuffer/size> | The number of bytes the system uses to hold encoded commands. This total doesn’t include memory for any commands that the system resets. Compare this size to the allocated size of the indirect command buffers. Choose the size of an indirect command buffer based on the number of commands you expect to execute inside it. |

For acceleration structures, you can add the following column:

| Column | Property | Description |
| --- | --- | --- |
| Size | <doc://com.apple.documentation/documentation/Metal/MTLAccelerationStructure/size> | The logical length, in bytes, of the acceleration structure. |

<a id="improve-your-metal-workload-with-insights"></a>

### Improve your Metal workload with Insights

Click the Insights button in the bottom right corner to open a popover of recommendations for the resources.

![A screenshot of the Insights popover showing recommendations related to unused resources.](<analyzing-memory-usage/fb9348e8d408ffe6c1e1a61e.png>)

<a id="limit-your-scope-with-filters"></a>

### Limit your scope with filters

Use the filter field at the bottom of the Memory viewer to adjust filtering criteria.
Type filter terms into the field, and the resources table displays any resources with labels that match those filter terms.

You can also click the filter button to add filters for specific kinds of resources, to limit the table to resources that the captured frame uses, and to limit the table to just volatile resources.

When there are two or more filter terms, you can click the filter button to choose whether to match any or all of the terms.
For any filter term, you can click it to choose to include or exclude resources that match that term.

<a id="group-and-sort-resources-to-detect-patterns"></a>

### Group and sort resources to detect patterns

By default, the resources table shows all resources in a single list.
You can click a column header to sort the table by that column in ascending or descending order. You can also group the resources by certain criteria.

Control-click an entry in the table to group the resources
by any of the following criteria:

- None:
  Restores the behavior to the default, which shows all resources in the table without grouping them.
- Type:
  Groups the resources into buffers, textures, heaps, or indirect command buffers.
- Allocated Size:
  Groups the resources by their actual size.
  The groupings are based on a logarithmic scale. Use this criteria to find the largest resources in your app.
- Storage Mode:
  Groups the resources by the storage mode you select when creating each resource.
- Command Buffer:
  Groups the resources based on which command buffers reference them.
  Use this criteria to determine which commands are referencing which resources.
- Command Encoder:
  Groups the resources according to commands that use a specific command encoder.
  Use this criteria to understand the behavior of your specific compute and render passes.

From this same context menu, you can also choose to sort by a specific criteria, which is equivalent to clicking a column heading for sorting.

<a id="get-more-information-about-a-specific-resource"></a>

### Get more information about a specific resource

You can also get more information about a specific resource by Control-clicking it and selecting Get Info.

For example, for a texture, the additional information shows details specific to that texture, such as its pixel format and dimensions.
To see the contents of the texture, double-click it.

<a id="export-a-memory-report"></a>

### Export a memory report

To share the data in the Memory viewer, you can export it in the following ways:

- Export a GPU trace:
  Choose File > Export and select a location to save the GPU trace file.
  You can then open the trace file later.
- Export a comma-separated values (CSV) file:
  Choose Editor > Export Memory Report to generate the CSV file.
  The resulting file has all of the columns you see in the resource view.
  You can open this file in Numbers or another spreadsheet app.

---

Copyright © 2026 Apple Inc. All rights reserved. | [Terms of Use](https://www.apple.com/legal/internet-services/terms/site.html) | [Privacy Policy](https://www.apple.com/privacy/privacy-policy)
