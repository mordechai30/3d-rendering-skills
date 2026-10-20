Source: [https://developer.apple.com/documentation/xcode/analyzing-draw-command-and-compute-dispatch-performance-with-gpu-counters](<https://developer.apple.com/documentation/xcode/analyzing-draw-command-and-compute-dispatch-performance-with-gpu-counters>)

<a id="analyzing-draw-command-and-compute-dispatch-performance-with-gpu-counters"></a>

# Analyzing draw command and compute dispatch performance with GPU counters

Identify issues within your frame capture by examining performance counters.

<a id="overview"></a>

## Overview

The Performance Statistics viewer displays counters to help you understand the automatically generated insights for hotspots and bottlenecks so you can improve GPU performance.
GPU performance counters are granular statistics that relate to the specific render, compute, or blit work your app performed in the captured frame.

![A screenshot of the Performance Statistics viewer displaying GPU counters in a table.](<analyzing-draw-command-and-compute-dispatch-performance-with-gpu-counters/9b776cae6ec47287efe76cb3.png>)

<a id="show-columns-for-performance-counters"></a>

### Show columns for performance counters

Control-click a column header to show and hide counter value columns for median, maximum, and total values.
You can view the following columns:

- Draw:
  The statistics for a command.
  For percentages like Vertex Stage Time, it measures the percentage of samples that the vertex stage uses for that draw.
- Encoder:
  The statistics for a pass.
  For percentages like Vertex Stage Time, it measures the percentage of samples that the vertex stage uses for all draws in the render pass.
- Median:
  The median counter value across all passes in the GPU trace.
- Max:
  The maximum counter value across all passes in the GPU trace.
- Total:
  The total of counter values for all passes in the GPU trace.

<a id="check-counters-data-for-anomalies"></a>

### Check counters data for anomalies

Move the pointer over a counter to reveal its description.

![A screenshot showing the tooltip for a counter when the pointer hovers over a table row.](<analyzing-draw-command-and-compute-dispatch-performance-with-gpu-counters/024d863450e3ddbc5fda3880.png>)

By analyzing values that may be hotspots, counters can suggest a specific cause of your app’s performance problem.
For example, if the number of vertices is twice as high as you expect, it’s likely that your code has duplicate meshes or render encoder draw calls.

<a id="limit-your-scope-with-filters"></a>

### Limit your scope with filters

Use the filter field at the bottom of the table to adjust filtering criteria by typing filter terms into it.
The table shows individual counters and groups of counters with names that match those filter terms.

When there are two or more filter terms, you can click the filter button to choose whether to match any or all of the terms.
For any filter term, you can click it to choose to include or exclude counters that match the term.

---

Copyright © 2026 Apple Inc. All rights reserved. | [Terms of Use](https://www.apple.com/legal/internet-services/terms/site.html) | [Privacy Policy](https://www.apple.com/privacy/privacy-policy)
