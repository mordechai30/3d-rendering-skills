Source: [https://developer.apple.com/documentation/xcode/analyzing-draw-command-and-compute-dispatch-performance-with-pipeline-statistics](<https://developer.apple.com/documentation/xcode/analyzing-draw-command-and-compute-dispatch-performance-with-pipeline-statistics>)

<a id="analyzing-draw-command-and-compute-dispatch-performance-with-pipeline-statistics"></a>

# Analyzing draw command and compute dispatch performance with pipeline statistics

Identify issues within your frame capture by examining pipeline statistics.

<a id="overview"></a>

## Overview

The Pipeline Statistics viewer displays each shader stage in your pipeline state, the amount of time it took to complete, and the GPU activities it performed during that time.

![A screenshot of the Pipeline Statistics viewer showing statistics for each shader and timing comparison across commands using the pipeline state.](<analyzing-draw-command-and-compute-dispatch-performance-with-pipeline-statistics/1d96a3d9fb9bddbdb74cc4b0.png>)

<a id="interpret-the-gpu-activities"></a>

### Interpret the GPU activities

Various GPU activities appear with bar charts for compiler statistics and runtime profiling statistics.

![A screenshot of the statistics for a shader. The top portion shows the timing by operations, and the bottom portion shows the number of instructions by operations.](<analyzing-draw-command-and-compute-dispatch-performance-with-pipeline-statistics/bbaeaf2e8bf5e9cd07d5f850.png>)

| GPU activity | Explanation and recommendations |
| --- | --- |
| ALU | The amount of time that the GPU spends in the arithmetic logic unit. Change floats to half-floats where possible to reduce the time in the ALU. Also, try to minimize your use of complex instructions like `sqrt`, `sin`, `cos`, and `recip`. |
| Memory | The amount of time that the GPU spends waiting for access to your app’s buffers or texture memory. Reduce time by downsampling textures, or, if you’re not spending much time in memory, improve your texture resolution instead. |
| Control flow | The amount of time that the GPU spends in conditional, increment, or jump instructions as a result of branches or loops in your shader. Use a constant iteration count to minimize control flow time for loops because the Metal compiler can generate optimized code in those cases. |
| Synchronization | The amount of time that the GPU spends waiting for a required resource or event before execution can begin. Synchronization types are described below. |
| Synchronization (wait memory) | The amount of time that the GPU spends waiting for dependent memory accesses, such as texture sampling or buffer read/write. |
| Synchronization (wait pixel) | The amount of time that the GPU spends waiting for underlying pixels to release resources. In addition to color attachments, pixels can come from depth or stencil buffers or user-defined resources. Blending is a common cause of pixel waiting. Use raster order groups to reduce the wait time. |
| Synchronization (barrier) | The amount of time that the GPU spends when a thread reaches a barrier and the GPU waits for remaining threads in the same group to arrive at the barrier before proceeding. |
| Synchronization (atomics) | The amount of time that the GPU spends on atomic instructions. |

<a id="inspect-the-gpu-time-of-the-commands-in-the-pass"></a>

### Inspect the GPU time of the commands in the pass

The bottom portion of the Pipeline Statistics viewer displays the GPU time in the Total column for each command in the pass so you can compare their respective elapsed times.

![A screenshot of the timing comparison across commands using the pipeline state.](<analyzing-draw-command-and-compute-dispatch-performance-with-pipeline-statistics/6199da18220fa31c02919027.png>)

---

Copyright © 2026 Apple Inc. All rights reserved. | [Terms of Use](https://www.apple.com/legal/internet-services/terms/site.html) | [Privacy Policy](https://www.apple.com/privacy/privacy-policy)
