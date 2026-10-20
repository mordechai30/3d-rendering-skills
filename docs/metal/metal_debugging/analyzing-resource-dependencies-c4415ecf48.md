Source: [https://developer.apple.com/documentation/xcode/analyzing-resource-dependencies](<https://developer.apple.com/documentation/xcode/analyzing-resource-dependencies>)

<a id="analyzing-resource-dependencies"></a>

# Analyzing resource dependencies

Avoid unnecessary work in your Metal app by understanding the relationships between resources.

<a id="overview"></a>

## Overview

The Dependencies viewer provides a graphical representation of the structure of your GPU trace and allows you to see the relationships between resources and the encoders that access them.
It also highlights the manual synchronizations you use between encoders, and indicates any unnecessary work by showing you all the unused resources in your frame.

![A screenshot of the Dependencies viewer, which includes a dependency graph view, a sidebar, and a control bar.](<analyzing-resource-dependencies/b317680c026945042f0502c1.png>)

<a id="inspect-the-graph-at-different-levels-of-detail"></a>

### Inspect the graph at different levels of detail

At the highest level, the Dependencies viewer shows the overall structure of your frame.
At this level, you can see the graph of command encoders inside command buffers.
You can also see all of the passes in your frame.
Each pass includes a thumbnail preview of its work, as well as the number of resources that it consumed or produced.
At this level, you can see whether data is flowing and whether there’s synchronization between passes.

![A screenshot of the Metal debugger’s Dependencies viewer showing the dependency graph with a low level of detail.](<analyzing-resource-dependencies/734eb8b687bfeb9fcc20aa07.png>)

As you zoom in to the next level, the Dependencies viewer expands the resources for each pass.
Additionally, each resource can have icons above and below it that indicate the consuming and producing actions.
For attachments in a render pass, the icons refer to the load and store actions.
Otherwise, they refer to general resource read-and-write operations.
At this level, you can also view which resources are introducing data flow or synchronization between passes.

![A screenshot of the Metal debugger’s Dependencies viewer showing the dependency graph with a medium level of detail.](<analyzing-resource-dependencies/d10e0a1d16bb611e4d4d48f3.png>)

As you zoom in more, the Dependencies viewer shows larger thumbnails and metadata for the resources.

![A screenshot of the Metal debugger’s Dependencies viewer showing the dependency graph with a high level of detail.](<analyzing-resource-dependencies/3ac4f85fa7826f451075093e.png>)

<a id="view-a-resources-consuming-and-producing-actions"></a>

### View a resource’s consuming and producing actions

The consuming and producing actions above and below a resource help you understand the resource accesses in a given pass at a quick glance.

For textures in a render pass, the actions refer to the load and store actions for each attachment.

For a multisample render pass, the store action may affect the storing for both the multisample and the resolve textures.
With <doc://com.apple.documentation/documentation/Metal/MTLStoreAction/storeAndMultisampleResolve>, the multisample texture shows a store action and the resolve texture shows a store action.
With <doc://com.apple.documentation/documentation/Metal/MTLStoreAction/multisampleResolve>, the multisample texture shows a don’t-care action and the resolve texture shows a store action.

Otherwise, the Dependencies viewer annotates the actions with generic read-and-write operations.

<a id="analyze-the-data-flow-and-synchronization-dependencies"></a>

### Analyze the data flow and synchronization dependencies

The Dependencies viewer displays two categories of dependencies between passes:

- Solid lines depict data flow. A previous pass produced data and a later pass consumes it.
- Dashed lines depict synchronization. There’s no data flow, but there’s a relationship between the two passes.

For example, a compute pass reading from a texture that a previous render encoder wrote has data flow between the two passes.

Additionally, a render pass that clears an attachment on load has no data dependency on any pass that previously modified the texture.
However, that render pass needs to wait until the previous passes finish modifying the texture — a synchronization.

<a id="choose-a-mode-for-viewing-dependencies"></a>

### Choose a mode for viewing dependencies

You can use the Dependencies viewer to choose different modes for visualization, each with a different subset of edges:

- All: Shows all edges from synchronization primitives, and tracked and untracked resources.
- Synchronzation: Shows dashed synchronization edges from synchronization primitives and tracked resources.
- Data Flow: Shows solid data-flow edges from tracked or untracked resources.

<a id="pin-resources-from-the-resource-pile"></a>

### Pin resources from the resource pile

To maintain a compact graph, the Dependencies viewer attempts to keep a few interesting resources visible on the graph and hide the rest in a pile under each pass. Clicking the pile opens a popover of the resources.

![A screenshot of the Resources popover at a pass in the Dependencies viewer.](<analyzing-resource-dependencies/ae3863894f14e2a225d32a9b.png>)

You can click the button to the right of each resource to pin or unpin it.

<a id="get-more-information-about-a-pass"></a>

### Get more information about a pass

Clicking any pass in the Dependencies viewer selects it and displays additional information about the pass in the sidebar.
You can also determine which resources the pass consumes or produces:

- For a resource the pass consumes, the Dependencies viewer suggests the pass that most recently modified the resource.
- For a resource the pass produces, the Dependencies viewer suggests the passes that later consume the data in the resource.

<a id="get-more-information-about-a-resource"></a>

### Get more information about a resource

Clicking any resource in the Dependencies viewer selects it and displays additional information about the resource in the sidebar.
You can also see the passes that last produced, or will later consume, the data in the resource.

When you select a resource, the Dependencies viewer highlights any related resources.
For example, when you select a texture view, it highlights the parent textures.
When you select a heap, it highlights the resources from the heap.

<a id="improve-your-metal-workload-with-insights"></a>

### Improve your Metal workload with Insights

Click the Insights button in the bottom right corner to open a popover of recommendations in the Dependencies viewer.

![A screenshot of the Insights popover in the Dependencies viewer.](<analyzing-resource-dependencies/f6d4374afe49c0b0f697ad94.png>)

<a id="limit-your-scope-with-filters"></a>

### Limit your scope with filters

Use the filter field at the bottom of the Dependencies viewer to adjust the graph’s filtering criteria.
Type filter terms into the field and the Dependencies viewer displays any related passes that match the filter terms.
In addition, when filtering by a resource, you can find passes that consume or produce the resource.

<a id="search-for-specific-elements"></a>

### Search for specific elements

Choose Find > Find to display the search bar above the Dependencies viewer.
You can type search terms into the search bar’s text field to find matching passes and resources.

For any search term, you can click it and choose to include or exclude elements that match the term.

The two arrow buttons to the right of the text field let you move to the previous or the next matching element in the Dependencies viewer.

---

Copyright © 2026 Apple Inc. All rights reserved. | [Terms of Use](https://www.apple.com/legal/internet-services/terms/site.html) | [Privacy Policy](https://www.apple.com/privacy/privacy-policy)
