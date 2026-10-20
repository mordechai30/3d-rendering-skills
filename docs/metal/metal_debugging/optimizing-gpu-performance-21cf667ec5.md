Source: [https://developer.apple.com/documentation/xcode/optimizing-gpu-performance](<https://developer.apple.com/documentation/xcode/optimizing-gpu-performance>)

<a id="optimizing-gpu-performance"></a>

# Optimizing GPU performance

Find and address performance bottlenecks using the Metal debugger.

<a id="overview"></a>

## Overview

Apple GPUs run vertex, fragment, and compute tasks in parallel whenever possible.
The Metal debugger offers ways to inspect the passes running with overlap, which you can use to find bottlenecking tasks in GPU-bound workloads.
In addition, the profiler measures performance statistics by sampling your shaders to reveal hot spots.

If you notice any performance issues while running your app, you can use the Metal debugger to find and investigate bottlenecks.
First, configure your build to include shader source code (see [Building your project with embedded shader sources](./building-your-project-with-embedded-shader-sources-ef9cf22fd2.md)).
Then, take a frame capture of your app when you notice the visual artifact that you want to debug (see [Capturing a Metal workload in Xcode](./capturing-a-metal-workload-in-xcode-2364f9433b.md)).

<a id="gather-performance-data"></a>

### Gather performance data

When you enable the Profile after Replay option, the Metal debugger automatically begins gathering performance data after replaying the workload.
Alternatively, you can click the Profile button on the Summary viewer to gather performance data.

![A screenshot of the Metal debugger showing the Summary viewer. The Profile button and the button to induce GPU performance state are highlighted.](<optimizing-gpu-performance/ae815bb9d8343c5df3dd1d60.png>)

The performance state of the GPU is important when profiling because it affects how fast the system executes the workload.
Factors that affect the performance state include thermals and system settings.

By default, the Metal debugger profiles the workload with the same GPU performance state at capture time, so the performance is typically similar to what you observe on the device.
However, you can induce a specific GPU performance state as you make a profile in the Metal debugger by clicking the GPU Profiler button in the debug bar.

For more information on GPU performance state, see [Discover Metal debugging, profiling, and asset creation tools](https://developer.apple.com/videos/play/wwdc2021/10157/?time=476).

![A screenshot of the Metal debugger’s Performance timeline that highlights the GPU Profiler popover, which has two menus for Performance State and GPU Execution Mode. The menus show Medium and Concurrent, respectively.](<optimizing-gpu-performance/9e5f25378d85a57cabfd4302.png>)

You can switch between different GPU Execution Modes, including Concurrent and Serial, by clicking the GPU Profiler button in the debug bar.
By default, the Metal debugger profiles the workload in Concurrent mode.
This allows the GPU to overlap the vertex, fragment, and compute tasks so they can finish as quickly as possible.
In Serial mode, the Metal debugger forces each pass to run only after the previous pass finishes,
which adds precision to the data report for each pass without overlap, but it doesn’t represent runtime performance.

<a id="find-performance-bottlenecks-with-the-performance-timeline"></a>

### Find performance bottlenecks with the Performance timeline

The Performance timeline in the Metal debugger can help you find expensive tasks and performance bottlenecks in the captured workload.
Open the Performance timeline by clicking the Performance button in the Debug navigator.

![A screenshot of the Metal debugger’s Performance timeline showing the Vertex, Fragment, Compute, and Counters tracks.](<optimizing-gpu-performance/eaa5762ebf0a3e15e3ba3e90.png>)

The Timeline navigator on the left side of the window lists all profiled passes, pipeline states, and GPU Commands with their shader profiler cost.

The top section has the Vertex, Fragment, and Compute GPU tracks, which display the beginning time and duration of individual passes running with overlap.
Below the GPU tracks are the aggregated shader tracks that combine the individual shaders.
You can view the timeline of individual shaders in a waterfall-like fashion by expanding the aggregated shader tracks.

The bottom section has a separate Counters timeline, which includes GPU counters such as Occupancy, Limiter, and Bandwidth.
The counters can help you diagnose performance bottlenecks.
You can focus on counter subsets by switching between different counter tabs.
For more information, see [Analyzing Apple GPU performance using a visual timeline](./analyzing-apple-gpu-performance-using-a-visual-timeline-992d237e3a.md).

<a id="get-detailed-performance-metrics-for-passes-and-draws"></a>

### Get detailed performance metrics for passes and draws

You can view performance counter statistics from your app’s passes or commands in the GPU trace.
Open the Performance counters by clicking the Counters tab above the Performance timeline.

![A screenshot of the Metal debugger’s Performance counters listing all the encoders and their counters.](<optimizing-gpu-performance/244c09d1458b3903d4884efd.png>)

The Metal debugger derives the shader profiler time by tracing the shader instructions when running the workload with overlap.
In a shader-bound workload, sorting the table by shader profiler time can point you to the overall most expensive pass or draw.
In addition, the Metal debugger measures the detailed counters from each pass or command in isolation.
You can also choose different sets of counters in the top bar for a more focused view.
For more information, see [Analyzing Apple GPU performance using counter statistics](./analyzing-apple-gpu-performance-using-counter-statistics-44d3b01c31.md).

<a id="group-commands-by-pipeline-states-in-the-debug-navigator"></a>

### Group commands by pipeline states in the Debug navigator

For a different perspective in viewing the Metal commands, click the Outline popup menu in the Debug navigator and select Group by Pipeline State to view a list of pipeline states.

![An Xcode screenshot of the Debug navigator showing all the pipeline states in the captured workload sorted from the most to the least expensive.](<optimizing-gpu-performance/93bbb008ea7eafc98e673e7e.png>)

With profiling data, the Debug navigator displays the percentage of samples from shaders of each pipeline state when running the workload with overlap.
In a shader-bound workload, this sorted list of pipeline states is helpful in identifying the most expensive pipeline state.
Expanding a pipeline state allows you to find a list of commands that use that state.

You can also quickly view the shader source code and per-line profiling statistics by selecting a shader from a pipeline state in the list.

For more information on the Debug navigator, see [Analyzing your Metal workload](./analyzing-your-metal-workload-1522098efa.md).

<a id="optimize-shaders-with-per-line-shader-profiling-statistics"></a>

### Optimize shaders with per-line shader profiling statistics

After opening a shader, you can find the time breakdown for the shader in the pipeline state.

![An Xcode screenshot of the Shader editor showing a call tree in the Debug navigator, and per-line shader profiling data next to the source code.](<optimizing-gpu-performance/d7397e7d9d68db0ccccd181a.png>)

The left sidebar allows you to inspect the shader source files and profiling call tree.
With the call tree, you can find performance hot spots by the weights of each frame.

In the gutter of the shader source code, you can find weights next to the lines of code.
The pie chart to the right of each weight contains performance statistics to help you improve the shader code.

For example, when you observe an expensive line of code with a high percentage for memory sample, it may be taking time to read texture data.
To reduce the shader time, if it’s less expensive to compute the value than reading it from a texture, you can modify the code to calculate it in the shader.

After making changes to the shader source code, click the Reload Shaders button in the debug bar to refresh the profiling statistics.
You can verify whether the changes help with the overall performance by observing the new total GPU time and the tracks in the Performance timeline.

> Important: Changes to your shader source code exist only within the Metal debugger.
> Your original shader source code doesn’t change.
> Make sure that you copy your changes to your original shader source code.

For more information on interpreting the per-line shader profiling statistics, see [Inspecting shaders](./inspecting-shaders-27f9d3e31a.md).

<a id="inspect-shader-performance-with-the-shader-cost-graph"></a>

### Inspect shader performance with the shader cost graph

> Important: The shader cost graph feature is available for iOS devices with A17 Pro or later, and Mac computers with M3 or later.

You can quickly find and triage expensive pipeline states and shaders by using the shader cost graph. Select a pipeline state in the Timeline navigator, and then click the Shaders tab.

![A screenshot of the Metal debugger’s shader cost graph.](<optimizing-gpu-performance/f2355fe0bf1abbcecd78086a.png>)

You can inspect the percentage cost of the shader function calls with the flame graph in the top section, and select function calls to jump directly to the source code.

For more information, see [Analyzing Apple GPU performance using the shader cost graph](./analyzing-apple-gpu-performance-using-shader-cost-graph-a17-m3-c871eb20be.md).

<a id="understand-simd-group-execution-with-the-performance-heat-maps"></a>

### Understand SIMD group execution with the performance heat maps

> Important: The performance heat maps feature is available for iOS devices with A17 Pro or later, and Mac computers with M3 or later.

You can quickly find and inspect the execution of your shader source code with the performance heat maps. Select an encoder, a pipeline state, or a GPU command in the Timeline navigator, and then click the Heat Maps tab.

![A screenshot of the Metal debugger’s performance heat maps.](<optimizing-gpu-performance/a8123638eeeaf5564053db7a.png>)

The top section shows various heat maps graphing statistical information about GPU threads, such as the cost, the divergence, and the number of instructions.

The bottom section shows the shader execution history of GPU threads on a timeline, including function call stacks and thread states.

For more information, see [Analyzing Apple GPU performance with performance heat maps](./analyzing-apple-gpu-performance-using-performance-heatmaps-a17-m3-7f49e8c741.md).

<a id="save-the-performance-data-to-your-development-system"></a>

### Save the performance data to your development system

You can save your app’s Metal workload performance data as a GPU trace for later analysis by choosing File > Export, and selecting the Embed performance data checkbox in the dialog. This allows you to view just the performance data instead of replaying the GPU trace on a device.

![A screenshot of a Metal debugger save dialog in Xcode for a performance data-trace file. The dialog has the name Deferred Lighting in the Export as field and a single checkbox with the label, Embed performance data, which a person selected.](<optimizing-gpu-performance/fda37cb42d5fa2d8fc054a21.png>)

You can open the GPU trace on any Mac — not just your development system — because it doesn’t require a compatible device to replay the trace.
Optionally, you can replay the GPU trace by selecting a compatible device.

For more information, see [Replaying a GPU trace file](./replaying-a-gpu-trace-file-cfd2b54be7.md).

---

Copyright © 2026 Apple Inc. All rights reserved. | [Terms of Use](https://www.apple.com/legal/internet-services/terms/site.html) | [Privacy Policy](https://www.apple.com/privacy/privacy-policy)
