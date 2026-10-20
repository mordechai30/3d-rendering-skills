Source: [https://developer.apple.com/documentation/xcode/inspecting-pipeline-states](<https://developer.apple.com/documentation/xcode/inspecting-pipeline-states>)

<a id="inspecting-pipeline-states"></a>

# Inspecting pipeline states

Determine how your render and compute passes behave by examining their properties.

<a id="overview"></a>

## Overview

The Metal debugger allows you to inspect a pipeline state with the Pipeline State viewer.
Double-click a pipeline state to open it and view its associated properties in a table.

![A screenshot of the Pipeline State viewer displaying the pipeline state’s properties hierarchically.](<inspecting-pipeline-states/2483b0f41a62fd6764cccbfb.png>)

In the screenshot above, the name of the pipeline state, G-buffer Creation, appears above the table.
To the right of the name, you can click the Reveal in Memory button or the Reveal in Timeline button to open the Memory viewer or the Performance timeline, respectively, which both highlight the pipeline state.

The table displays the properties of your pipeline state in a logical hierarchy.
Click the disclosure controls on the left to expand the groups to view more information.
Using the table, you can quickly inspect the properties of <doc://com.apple.documentation/documentation/Metal/MTLRenderPipelineState> or <doc://com.apple.documentation/documentation/Metal/MTLComputePipelineState>.

<a id="limit-your-scope-with-filters"></a>

### Limit your scope with filters

Use the filter field at the bottom of the Pipeline State viewer to adjust the filtering criteria by typing filter terms into it.
Then the table displays the related pipeline state properties that match the filter terms, and highlights the matches.

![A screenshot of the Pipeline State viewer filtering for the term pixel. The list displays the matching properties hierarchically.](<inspecting-pipeline-states/cd93d6815b48f41cfa9d4782.png>)

When there are two or more filter terms, you can click the filter button to choose whether to match any or all of the terms.

---

Copyright © 2026 Apple Inc. All rights reserved. | [Terms of Use](https://www.apple.com/legal/internet-services/terms/site.html) | [Privacy Policy](https://www.apple.com/privacy/privacy-policy)
