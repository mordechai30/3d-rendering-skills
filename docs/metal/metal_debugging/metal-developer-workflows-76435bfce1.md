Source: [https://developer.apple.com/documentation/xcode/metal-developer-workflows](<https://developer.apple.com/documentation/xcode/metal-developer-workflows>)

<a id="metal-developer-workflows"></a>

# Metal developer workflows

Locate and fix issues related to your app’s use of the Metal API and GPU functions.

<a id="overview"></a>

## Overview

Metal comes with a comprehensive suite of advanced developer tools to help you debug and optimize your Metal apps.

<a id="runtime-diagnostics"></a>

### Runtime diagnostics

You can enable API Validation when running your app to check for incorrect Metal API usage.
For more information, see [Validating your app’s Metal API usage](./validating-your-apps-metal-api-usage-e2d8d3d7a5.md).

Enable Shader Validation when running your app to check for issues like out-of-bounds memory access, missing `useResource` calls, and stack overflows.
For more information, see [Validating your app’s Metal shader usage](./validating-your-apps-metal-shader-usage-5a1d24e1b0.md).

The Metal Performance HUD offers a visual overlay to catch performance issues while your app is running.
For more information, see [Monitoring your Metal app’s graphics performance](./monitoring-your-metal-apps-graphics-performance-89128c4b39.md).

<a id="runtime-performance-analysis"></a>

### Runtime performance analysis

The Metal system trace tool in Instruments provides a visual timeline of the parallel work on the CPU and the GPU, and the memory usage of your Metal app.

![An Instruments screenshot displaying a capture in the Game Performance template.](<metal-developer-workflows/1cab07c75dafd7b3b3e8f085.png>)

You can begin profiling with the Game Performance template (see [Analyzing the performance of your Metal app](./analyzing-the-performance-of-your-metal-app-54840a27ed.md)) or the Game Memory template (see [Analyzing the memory usage of your Metal app](./analyzing-the-memory-usage-of-your-metal-app-261300bc8d.md)).

<a id="advanced-metal-debugging-and-profiling"></a>

### Advanced Metal debugging and profiling

The Metal debugger in Xcode provides advanced tools for debugging and profiling your Metal app.

![A screenshot of the Metal debugger showing the Bound Resources viewer and attachments for a draw command.](<metal-developer-workflows/816c9cdf86be909c562f789b.png>)

You can get summaries of your Metal workload with the Dependencies viewer and the Memory viewer, inspect individual resources, and selectively debug your shaders.
For more information on debugging, see [Investigating visual artifacts](./investigating-visual-artifacts-caaf4d188b.md).

In addition, you can optimize your Metal app by drilling down performance bottlenecks with the Performance timeline and the per-line shader profiling results.
For more information on profiling, see [Optimizing GPU performance](./optimizing-gpu-performance-21cf667ec5.md).

Learn more about [Metal debugger](./metal-debugger-2478b0d03a.md).

<a id="topics"></a>

## Topics

<a id="project-preparation-for-debugging"></a>

### Project preparation for debugging

Make your Metal app easier to debug by taking a few extra steps as you develop your code.

[Building your project with embedded shader sources](./building-your-project-with-embedded-shader-sources-ef9cf22fd2.md)

Prepare to debug your project’s shaders by including source code in the build.

[Naming resources and commands](./naming-resources-and-commands-8d146531da.md)

Enhance the debugging of your Metal app using labels and grouping.

[Creating and using custom capture scopes](./creating-and-using-custom-capture-scopes-4be07d3028.md)

Capture specific GPU commands by using custom capture scopes.

<a id="runtime-diagnostics-1"></a>

### Runtime diagnostics

Learn how to use runtime tools to discover potential issues in your Metal app.

[Inspecting live resources at runtime](./inspecting-live-resources-at-runtime-44e8d525fa.md)

Validate your resources by viewing the contents of your textures and buffers while debugging your Metal app.

[Validating your app’s Metal API usage](./validating-your-apps-metal-api-usage-e2d8d3d7a5.md)

Catch runtime issues in your Metal app using API Validation.

[Validating your app’s Metal shader usage](./validating-your-apps-metal-shader-usage-5a1d24e1b0.md)

Catch common shader runtime issues using Shader Validation.

[Monitoring your Metal app’s graphics performance](./monitoring-your-metal-apps-graphics-performance-89128c4b39.md)

Catch performance issues using the Metal Performance HUD while your app runs.

[Customizing the Metal Performance HUD](./customizing-metal-performance-hud-4877b4e388.md)

Modify the appearance of your Metal heads-up display to monitor your graphics performance.

[Understanding the Metal Performance HUD metrics](./understanding-metal-performance-hud-metrics-e8fc6cec3d.md)

Learn what each of the metrics reported by the heads-up display indicates.

[Gaining performance insights with the Metal Performance HUD](./gaining-performance-insights-with-metal-performance-hud-69b1f2a938.md)

Catch potential performance issues while your app runs using the Metal heads-up display.

[Generating performance reports with the Metal Performance HUD](./generating-performance-reports-with-metal-performance-hud-6933ed812d.md)

Record your app’s performance using the heads-up display.

<a id="counters"></a>

### Counters

Get references for the set of performance metrics available across Metal tools.

[Finding your Metal app’s GPU occupancy](./finding-your-metal-apps-gpu-occupancy-2f9a2827c4.md)

Understand the GPU usage for executing shaders by using occupancy.

[Reducing shader bottlenecks](./reducing-shader-bottlenecks-2163cf08ba.md)

Identify and minimize congestion points in a GPU’s subsystems by checking its limiter and utilization counters.

[Measuring the GPU’s use of memory bandwidth](./measuring-the-gpus-use-of-memory-bandwidth-1ea3f05873.md)

Check whether your Metal app correctly reads and writes to memory by measuring the GPU’s memory bandwidth.

---

Copyright © 2026 Apple Inc. All rights reserved. | [Terms of Use](https://www.apple.com/legal/internet-services/terms/site.html) | [Privacy Policy](https://www.apple.com/privacy/privacy-policy)
