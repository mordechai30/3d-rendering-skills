Source: [https://developer.apple.com/documentation/xcode/inspecting-the-bound-resources-for-a-command](<https://developer.apple.com/documentation/xcode/inspecting-the-bound-resources-for-a-command>)

<a id="inspecting-the-bound-resources-for-a-command"></a>

# Inspecting the bound resources for a command

Discover issues by examining the bound resources at any point in an encoder.

<a id="overview"></a>

## Overview

Metal’s render and compute encoders allow you to set pipeline states, bind resources, specify parameters, and encode GPU commands.
The Bound Resources viewer helps you determine the bound resources at any point in an encoder.

![A screenshot of the Bound Resources viewer, listing the bound resources.](<inspecting-the-bound-resources-for-a-command/7d9dd08af9b7b91d68fac478.png>)

<a id="inspect-bound-resources"></a>

### Inspect bound resources

The Bound Resources viewer displays the current set of bound resources in the encoder.
You can double-click a resource row to further inspect that resource.

![A screenshot of the table of bound resources for a draw command.](<inspecting-the-bound-resources-for-a-command/454adedda47be100e860548f.png>)

For a render pass, the Bound Resources viewer groups the resources in the following sections:

- **Render Pipeline:** The specified render pipeline state.
- **Execute Indirect:** The indirect command buffer (ICB) that the command executes from.
- **Vertex/Object/Mesh/Tile/Fragment Stage:** The resources in the corresponding stage. In addition, it includes the shader function. For the vertex and the mesh stage, it also includes the index buffer and output geometry.
- **Attachments:** The attachment textures.
- **Indirect:** The used indirect resources and those from the same heap. To use a resource, call <doc://com.apple.documentation/documentation/Metal/MTLRenderCommandEncoder/useResource(_:usage:stages:)> or <doc://com.apple.documentation/documentation/Metal/MTLRenderCommandEncoder/useHeap(_:stages:)>.

For a compute pass, the Bound Resources viewer groups the resources in the following sections:

- **Compute Pipeline:** The specified compute pipeline state.
- **Execute Indirect:** The indirect command buffer (ICB) that the command executes from.
- **Compute:** The resources in the compute pass.
- **Indirect:** The used indirect resources and those from the same heap. To use a resource, call <doc://com.apple.documentation/documentation/Metal/MTLComputeCommandEncoder/useResource(_:usage:)>, <doc://com.apple.documentation/documentation/Metal/MTLComputeCommandEncoder/useResources(_:usage:)>, <doc://com.apple.documentation/documentation/Metal/MTLComputeCommandEncoder/useHeap(_:)>, or <doc://com.apple.documentation/documentation/Metal/MTLComputeCommandEncoder/useHeaps(_:)>.

The Bound Resources viewer includes the following information for all resource types:

| Column | Property | Description |
| --- | --- | --- |
| Label | <doc://com.apple.documentation/documentation/Metal/MTLResource/label> | The label you set when creating the resource. Use this information to identify specific resources in your app. To learn how to name your resources, see <doc://com.apple.Xcode/documentation/Xcode/Naming-resources-and-commands>. |
| Type |  | An attribute to identify the location of the argument in the shader: buffer, texture, sampler, or threadgroup buffer index. |
| Allocated Size | <doc://com.apple.documentation/documentation/Metal/MTLResource/allocatedSize> | The actual allocated memory size for the resource. |
| Parameter Name |  | The name of the variable in the shader that binds to the resource. |
| Resource Usage |  | An indicator of whether the shader can read from or write to the resource. |
| Access |  | An indicator of whether the shader actually accesses the resource in the draw command or compute dispatch. |
| Insights |  | Possible problems or optimizations that might improve resource usage. |
| Shader Stages |  | The shader stages that use the resource (see <doc://com.apple.documentation/documentation/Metal/MTLRenderStages>). |

For textures, you can add the following columns:

| Column | Property | Description |
| --- | --- | --- |
| Pixel Format | <doc://com.apple.documentation/documentation/Metal/MTLTexture/pixelFormat> | The Metal pixel format you choose when creating the texture. |
| Type | <doc://com.apple.documentation/documentation/Metal/MTLTexture/textureType> | The texture’s subtype. |
| Width | <doc://com.apple.documentation/documentation/Metal/MTLTexture/width> | The width, in pixels, of the texture’s base mipmap. |
| Height | <doc://com.apple.documentation/documentation/Metal/MTLTexture/height> | The height, in pixels, of the texture’s base mipmap. |
| Depth | <doc://com.apple.documentation/documentation/Metal/MTLTexture/depth> | The depth, in pixels, of the texture’s base mipmap. |
| Slice | <doc://com.apple.documentation/documentation/Metal/MTLRenderPassAttachmentDescriptor/slice> | The slice of the texture for the render pass attachment. |
| Level | <doc://com.apple.documentation/documentation/Metal/MTLRenderPassAttachmentDescriptor/level> | The mipmap level of the texture for the render pass attachment. |
| Depth Plane | <doc://com.apple.documentation/documentation/Metal/MTLRenderPassAttachmentDescriptor/depthPlane> | The depth plane of the texture for the render pass attachment. |
| Array Length | <doc://com.apple.documentation/documentation/Metal/MTLTexture/arrayLength> | The number of slices in the texture array. |
| Mipmap Count | <doc://com.apple.documentation/documentation/Metal/MTLTexture/mipmapLevelCount> | The number of mipmap levels that the texture stores. |
| Sample Count | <doc://com.apple.documentation/documentation/Metal/MTLTexture/sampleCount> | The number of samples that each pixel stores. |
| Usage | <doc://com.apple.documentation/documentation/Metal/MTLTexture/usage> | Flags that indicate the actions a shader or app can perform on the texture. The more restricted the list, the more optimizations Metal can apply to the texture. |

For buffers, you can add the following columns:

| Column | Property | Description |
| --- | --- | --- |
| Length | <doc://com.apple.documentation/documentation/Metal/MTLBuffer/length> | The logical length, in bytes, of the buffer. |
| Offset |  | The location where the data begins, in bytes, from the start of the buffer. |

For functions, you can add the Library column to show the library that the app uses to create the function.

<a id="improve-your-metal-workload-with-insights"></a>

### Improve your Metal workload with Insights

Click the Insights button in the bottom right corner to open a popover of recommendations for the bound resources.

![A screenshot of the Insights popover showing two recommendations related to redundant buffer bindings.](<inspecting-the-bound-resources-for-a-command/2190b9c3f0c2d47a4e111543.png>)

<a id="inspect-resources-that-the-shaders-access"></a>

### Inspect resources that the shaders access

The shaders don’t necessarily access every bound resource in a draw command or compute dispatch.
This is very common in bindless workflows where shaders access only a small set of resources from a large heap.
The Bound Resources viewer provides a top-level filter for resources that the shaders actually access.

To apply the filter, click the Accessed button above the table to view only the accessed resources.

![A screenshot of the Bound Resources viewer highlighting the Accessed button.](<inspecting-the-bound-resources-for-a-command/8d908743d00114eb57a591b7.png>)

<a id="limit-your-scope-with-filters"></a>

### Limit your scope with filters

Use the filter field at the bottom of the Bound Resources viewer to adjust the filtering criteria by typing filter terms into it.
The table shows the related resources that match the filter terms.

You can also click the filter button to add filters for specific kinds of resources or for the used indirect resources.

When there are two or more filter terms, you can click the filter button to choose whether to match any or all of the terms.
For any filter term, you can click it to choose to include or exclude resources that match the term.

---

Copyright © 2026 Apple Inc. All rights reserved. | [Terms of Use](https://www.apple.com/legal/internet-services/terms/site.html) | [Privacy Policy](https://www.apple.com/privacy/privacy-policy)
