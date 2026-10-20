Source: [https://developer.apple.com/documentation/xcode/analyzing-non-apple-gpu-performance-using-counter-statistics](<https://developer.apple.com/documentation/xcode/analyzing-non-apple-gpu-performance-using-counter-statistics>)

<a id="analyzing-non-apple-gpu-performance-using-counter-statistics"></a>

# Analyzing non-Apple GPU performance using counter statistics

Optimize performance by examining counters for individual passes and commands.

<a id="overview"></a>

## Overview

> Important: The Counters viewer feature isn’t applicable to Apple GPUs.
> For Apple GPUs, see <doc://com.apple.Xcode/documentation/Xcode/Analyzing-Apple-GPU-performance-using-a-visual-timeline> and <doc://com.apple.Xcode/documentation/Xcode/Analyzing-Apple-GPU-performance-using-counter-statistics>.

The Counters viewer shows performance counters from your app’s passes or commands in the GPU trace.
These counters measure hardware-related activities on the GPU, ranging from memory bandwidth to the number of vertices, the number of rasterized fragments, and the texture-filtering limiter and utilization percentages.

![A screenshot of the Counters viewer, consisting of a counters timeline and a table for either passes or commands.](<analyzing-non-apple-gpu-performance-using-counter-statistics/79114511c3b8f81bedf363e7.png>)

The Metal debugger collects data from the passes running without overlap, so
only one pass runs at a time on the device when the profiler measures the performance.
Additionally, it includes deterministic counters that don’t vary by time, such as the number of vertices in a render pass.

<a id="view-different-counter-sets-for-passes-or-commands"></a>

### View different counter sets for passes or commands

At the top of the graph, you can click the Encoder or the Draw tab to choose to view the counters by pass or command granularity.
Then, you can choose which counter set to use for viewing the collection of counters.

<a id="find-a-pass-with-high-shader-gpu-time"></a>

### Find a pass with high shader GPU time

The height of the orange bar for each pass represents its shader GPU time.
The tallest bar corresponds to the pass that took the longest time to complete.
Minimize the duration of the long-running passes to optimize your app’s performance.

![A screenshot of the per-pass counters timeline. The pass with the longest shader GPU time is selected.](<analyzing-non-apple-gpu-performance-using-counter-statistics/889fb580ab36b07131d2a0bc.png>)

There are three render passes in the screenshot above, with the tallest bar for shader GPU time at the GBuffer Generation pass.
You can move the pointer over the bar to view the time and other information.
In the screenshot above, the shader GPU time for the GBuffer Generation pass reads 657.69 microseconds (μs).

<a id="view-performance-counters-in-the-assistant-editor"></a>

### View performance counters in the assistant editor

The assistant editor allows you to see additional information for individual passes and commands.
You can enable the assistant editor by clicking the Adjust Editor Options button and choosing the Assistant option.

![A screenshot of the Adjust Editor Options menu highlighting the Assistant menu item.](<analyzing-non-apple-gpu-performance-using-counter-statistics/cc86614685d1b73033ae619d.png>)

Selecting a pass or command shows its performance counters in the assistant editor.
If you see something other than performance counters, you can select Performance from the drop-down menu at the top left of the editor.

![A screenshot of the assistant editor drop-down menu highlighting the Performance menu item.](<analyzing-non-apple-gpu-performance-using-counter-statistics/bc60ba4b1684074f4a1c8ee1.png>)

The performance counters in the assistant editor let you inspect all the counters for a specific pass or command.
By analyzing values that may be hotspots, counters can suggest a specific cause of your app’s performance problem.
For example, if the number of vertices is twice as high as you expect, it’s likely that your code has duplicate meshes or render encoder draw calls.

![A screenshot of the Metal debugger showing the Counters viewer and the Performance Statistics viewer side by side.](<analyzing-non-apple-gpu-performance-using-counter-statistics/9fe104910135c732726f2f83.png>)

For more information, see [Analyzing draw command and compute dispatch performance with GPU counters](./analyzing-draw-command-and-compute-dispatch-performance-with-gpu-counters-acd7eae10b.md).

<a id="view-pipeline-statistics-for-a-command"></a>

### View pipeline statistics for a command

Selecting a command allows you to look at its pipeline statistics in the assistant editor.
You can select Pipeline Statistics from the Assistant Editor drop-down menu to view information about the pipeline state and its performance statistics.

![A screenshot of the assistant editor drop-down menu highlighting the Pipeline Statistics menu item.](<analyzing-non-apple-gpu-performance-using-counter-statistics/8288c6cb626552ca3d8750ab.png>)

The pipeline statistics in the assistant editor let you look at compiler statistics and runtime profiling statistics.
The top portion of the assistant editor area lists the time each pipeline stage took to complete in separate categories.
Below, it lists the commands that use the same pipeline stage, as well as their shader GPU time.

![A screenshot of the Metal debugger showing the Counters viewer and the Pipeline Statistics viewer side by side.](<analyzing-non-apple-gpu-performance-using-counter-statistics/9255ace61f5050c89d9fd1f2.png>)

For more information, see [Analyzing draw command and compute dispatch performance with pipeline statistics](./analyzing-draw-command-and-compute-dispatch-performance-with-pipeline-statistics-c5e457f790.md).

Sometimes, counters data may only hint at a problem, and you can benefit by leveraging additional Metal tools.
For example, if your fragment shader time is unexpectedly high, you can use the Shader editor to discover which specific lines in your fragment shader are slowing down the execution.
For more information, see [Inspecting shaders](./inspecting-shaders-27f9d3e31a.md).

---

Copyright © 2026 Apple Inc. All rights reserved. | [Terms of Use](https://www.apple.com/legal/internet-services/terms/site.html) | [Privacy Policy](https://www.apple.com/privacy/privacy-policy)
