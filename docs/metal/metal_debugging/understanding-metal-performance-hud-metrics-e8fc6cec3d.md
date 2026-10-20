Source: [https://developer.apple.com/documentation/xcode/understanding-metal-performance-hud-metrics](<https://developer.apple.com/documentation/xcode/understanding-metal-performance-hud-metrics>)

<a id="understanding-the-metal-performance-hud-metrics"></a>

# Understanding the Metal Performance HUD metrics

Learn what each of the metrics reported by the heads-up display indicates.

<a id="overview"></a>

## Overview

The Metal Performance HUD provides a variety of performance metrics to help you spot performance issues, or find the perfect scope to capture in Xcode (see [Capturing a Metal workload in Xcode](./capturing-a-metal-workload-in-xcode-2364f9433b.md))
or in Instruments (see [Analyzing the performance of your Metal app](./analyzing-the-performance-of-your-metal-app-54840a27ed.md)).

> Note:
> To learn more about how to customize the Metal Performance HUD and enable various metrics, see <doc://com.apple.Xcode/documentation/Xcode/Customizing-metal-performance-hud>.

Below is a complete list of the Metal Performance HUD metrics:

- Metal Device:
  Shows the name of the <doc://com.apple.documentation/documentation/Metal/MTLDevice>.
- Rosetta Info:
  Shows the active architecture (x86\_64) if the app runs through the Rosetta translation layer.
- Layer Size and Composition:
  Shows the size of the layer and the present mode (direct or composited).
- Layer Scale and Pixel Format:
  Shows the content scale factor and pixel format of the layer.
- Memory:
  Shows the current amount of memory the process is using, and the <doc://com.apple.documentation/documentation/Metal/MTLDevice/currentAllocatedSize> of the `MTLDevice`.
- Thermal State:
  Shows the current <doc://com.apple.documentation/documentation/Foundation/ProcessInfo/thermalState-swift.property> of the machine.
- Screen Refresh Rate:
  Shows the current refresh rate of the display your app is on.
- Game Mode:
  Shows the state of Game Mode (on or off).
- FPS:
  Shows the rolling average of frames per second for the past 120 frames. FPS is calculated by dividing 1 second with the frame interval.
- FPS Graph:
  Shows a chart graphing the FPS for the past 120 frames.
- Frame Number:
  Shows the current frame number. In most cases this is the number of drawable presents since the app launch or last metric reset. This value counts interpolated frames when you enable frame interpolation.
- GPU Time:
  Shows the rolling average of GPU time for the past 120 frames. GPU time is calculated using the <doc://com.apple.documentation/documentation/Metal/MTLCommandBuffer/gpuStartTime> and <doc://com.apple.documentation/documentation/Metal/MTLCommandBuffer/gpuEndTime> of the command buffers that get scheduled by Metal for each frame.
- Present Delay:
  Shows the rolling average of present delay for the past 120 frames. Present delay is the interval between the time when you call `presentDrawable` to the time when the drawable hits the display.
- Frame Interval:
  Shows the rolling average of the on-glass time difference between two consecutive `MTLDrawables` for the past 120 frames.
- Frame Interval Graph:
  Shows a chart graphing the frame interval for the past 120 frames.
- Frame Interval Histogram:
  Shows a bucketed frame interval with a bar chart. The bucket size is the display refresh rate.
- Command Buffer and Encoder Count:
  Shows the number of scheduled command buffers and encoders, and their CPU encoding time for the last frame. The CPU time for encoders is the interval between the allocation of command encoder to the end of encoding.
- Shader Compiler:
  Shows the shader compiler activity including number of pipeline states, number of cached shaders, and number of compiled shaders and compilation time. Below the number of compiled shaders is a graph showing the compilation time for the past 120 frames.
- Disk Usage:
  Shows the disk bytes read, written, and logical writes as reported by system usage. To learn more, see <doc://com.apple.documentation/documentation/kernel/rusage_info_current>.

> Important:
> The metrics below require that you enable the encoder GPU time tracking feature. To learn more, see <doc://com.apple.Xcode/documentation/Xcode/Customizing-metal-performance-hud>.

- Encoder Time and GPU Timeline:
  Shows encoder GPU times for each type of encoder, and a GPU timeline graph. The GPU timeline shows the encoder durations on the GPU for the past three frames every second.
- Top Labeled Command Buffers:
  Shows the most GPU-intensive command buffers with a <doc://com.apple.documentation/documentation/Metal/MTLCommandBuffer/label> and excludes command buffers without a label.
- Top Labeled Encoders:
  Shows the most GPU-intensive encoders with a <doc://com.apple.documentation/documentation/Metal/MTLCommandEncoder/label> and excludes command encoders without a label.

> Important:
> The metrics below only appear when you use specific MetalFX effects in your app. To learn more about MetalFX, see <doc://com.apple.documentation/documentation/MetalFX>.

- MetalFX Scaling:
  Shows the scaling method of MetalFX (temporal, spatial, or denoising).
- MetalFX Scaling Input Resolution:
  Shows the input resolution of MetalFX scaling.
- MetalFX Scaling Target Resolution:
  Shows the target resolution of MetalFX scaling.
- MetalFX Exposure:
  Shows the exposure of the MetalFX effect.
- MetalFX Frame Interpolator:
  Shows the state of MetalFX frame interpolation (on or off).

> Important:
> The metrics below only appear when you evaluate your game through the Game Porting Toolkit evaluation environment. To learn more, see [Game Porting Toolkit](https://developer.apple.com/games/game-porting-toolkit/).

- GPTk Draw (GSTS):
  Shows the number of draw calls (`DrawInstanced`, `DrawIndexedInstanced`, `DrawInstancedIndirect`, and `DrawIndexedInstandedIndirect`) with a geometry stage and a tessellation stage.
- GPTk Draw (TS):
  Shows the number of draw calls (`DrawInstanced`, `DrawIndexedInstanced`, `DrawInstancedIndirect`, and `DrawIndexedInstandedIndirect`) with a tessellation stage.
- GPTk Draw (GS):
  Shows the number of draw calls (`DrawInstanced`, `DrawIndexedInstanced`, `DrawInstancedIndirect`, and `DrawIndexedInstandedIndirect`) with a geometry stage.
- GPTk Draw:
  Shows the number of draw calls (`DrawInstanced`, `DrawIndexedInstanced`, `DrawInstancedIndirect`, and `DrawIndexedInstandedIndirect`) that don’t use a geometry stage or a tessellation stage.
- GPTk Execute Indirect:
  Shows the number of indirect draw calls or dispatches (`DrawInstancedIndirect`, `DrawIndexedInstandedIndirect`, and `DispatchIndirect`) .
- GPTk Dispatch:
  Shows the number of dispatches (`Dispatch`).
- GPTk Dispatch Mesh:
  Shows the number of draw calls or dispatches (`DrawInstanced`, `DrawIndexedInstanced`, `DrawInstancedIndirect`, `DrawIndexedInstandedIndirect`, `Dispatch`, and `DispatchIndirect`) with a mesh stage.
- GPTk Copy Resource:
  Shows the number of resource copies (`CopyResource`, `CopyBufferRegion`, `UpdateSubResource`, `CopySubResourceRegion`, and `CopyTextureRegion`).
- GPTk Clear Resource:
  Shows the number of clears commands (`ClearRenderTargetView`, `ClearDepthStencilView`, and `ClearUnorderedAccessView`).
- GPTk Refit BVH:
  Shows the number of BVH refits.
- GPTk Build BVH:
  Shows the number of BVH builds.
- GPTk Display Rays:
  Shows the number of ray dispatches.
- GPTk Ray Query:
  Shows the number of ray queries.

---

Copyright © 2026 Apple Inc. All rights reserved. | [Terms of Use](https://www.apple.com/legal/internet-services/terms/site.html) | [Privacy Policy](https://www.apple.com/privacy/privacy-policy)
