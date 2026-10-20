Source: [https://developer.apple.com/documentation/xcode/monitoring-your-metal-apps-graphics-performance](<https://developer.apple.com/documentation/xcode/monitoring-your-metal-apps-graphics-performance>)

<!--
{
  "documentType" : "article",
  "framework" : "Xcode",
  "identifier" : "/documentation/Xcode/Monitoring-your-Metal-apps-graphics-performance",
  "metadataVersion" : "0.1.0",
  "role" : "article",
  "title" : "Monitoring your Metal app’s graphics performance"
}
-->

# Monitoring your Metal app’s graphics performance

Catch performance issues using the Metal Performance HUD while your app runs.

## Overview

The Metal Performance HUD (heads-up display) adds a real-time overlay to your app that displays and, optionally, logs common graphics performance information. The overlay helps you spot subtle performance issues, such as large variations in rendering time, so you can find the perfect scope to capture in Xcode (see [Capturing a Metal workload in Xcode](/documentation/Xcode/Capturing-a-Metal-workload-in-Xcode)) or in Instruments (see [Analyzing the performance of your Metal app](/documentation/Xcode/Analyzing-the-performance-of-your-Metal-app)).

![A screenshot of the Metal Performance HUD over a rendered scene from Metal.](<monitoring-your-metal-apps-graphics-performance/4a96ceeeb860e23a499e3fd0.png>)

By default, the top of the HUD shows the Metal device, resolution, an indicator for whether the present mode is direct or composited, the amount of memory allocated by the app and Metal, and whether Game Mode is turned on or off (see [Use Game Mode on Mac](https://support.apple.com/en-us/105118)).

The bottom section of the HUD shows the average frames per second (FPS), GPU time, and frame interval.
Below the frame interval is a chart graphing the frame interval from the past 120 frames.

![A cropped screenshot of the Metal Performance HUD showing the GPU, resolution, display scaling factor, present mode, and refresh rate.](<monitoring-your-metal-apps-graphics-performance/78c0f61b88c90bbe983e6cb2.png>)

You can also customize the HUD to include more metrics. To learn more, see [Customizing the Metal Performance HUD](/documentation/Xcode/Customizing-metal-performance-hud).

For more information about the metrics provided by the HUD, see [Understanding the Metal Performance HUD metrics](/documentation/Xcode/Understanding-metal-performance-hud-metrics).

### Enable the HUD and logging in Xcode

Follow these steps to enable the Metal Performance HUD using the runtime diagnostics options in the scheme settings:

1. In the Xcode toolbar, choose Edit Scheme from the Scheme menu. Alternatively, choose Product > Scheme > Edit Scheme.
   ![An Xcode screenshot that shows the Scheme menu with the Edit Scheme menu item highlighted.](<monitoring-your-metal-apps-graphics-performance/a55256943d58b3d482fbe28a.png>)
2. In the scheme action panel, select Run.
3. In the action setting tab, click Diagnostics.
4. Select Show Graphics Overview to enable the Metal Performance HUD, and click Close.
   ![A screenshot of Xcode scheme editor with the Show Graphics Overview option enabled and highlighted.](<monitoring-your-metal-apps-graphics-performance/d9e0bcfd32ddb3768cb976b1.png>)

Now, Xcode enables the Metal Performance HUD runtime each time you run your scheme.

You can also optionally enable the output of per-frame statistics to the console by selecting the Log Graphics Overview option.

![A screenshot of the Xcode scheme editor with the Log Graphics Overview option enabled and highlighted.](<monitoring-your-metal-apps-graphics-performance/6cef71f2f0dbb910b228b0ff.png>)

> Note: You need to select both the Show Graphics Overview and the Log Graphics Overview options to output per-frame statistics.

### Enable the HUD and logging with environment variables

You can enable the Metal Performance HUD and logging by setting the following environment variables on your Metal app:

- MTL_HUD_ENABLED=1:
  Enables the Metal Performance HUD.
- MTL_HUD_LOG_ENABLED=1:
  Enables logging of per-frame statistics.
  Requires `MTL_HUD_ENABLED=1`.
- MTL_HUD_LOG_SHADER_ENABLED=1:
  Enables logging of shader compilation activities.
  Requires `MTL_HUD_ENABLED=1`.

### Enable the HUD and logging on a device

You can enable the Metal Performance HUD and logging on an iOS, iPadOS, or tvOS device in the Developer settings by following these steps:

1. Open the Settings app.
2. Select Developer.
3. Under Graphics HUD, toggle the Show Graphics HUD option to enable the Metal Performance HUD.
4. Toggle the Log Graphics Performance option to enable logging.

The Metal Performance HUD appears for apps you build and install yourself to your development devices.

> Note: Your device needs to have a development provisioning profile for the Developer options to appear in the Settings app.

The following screenshot shows the options in iOS:

![A screenshot of the Developer settings in iOS, highlighting the toggles to enable the Metal Performance HUD overlay and logging.](<monitoring-your-metal-apps-graphics-performance/5fac992be697e92b51679df2.png>)

The following screenshot shows the options in tvOS:

![A screenshot of the Developer settings in tvOS, highlighting the toggles to enable the Metal Performance HUD overlay and logging.](<monitoring-your-metal-apps-graphics-performance/e23ef3cb7e9b95fba6ca3ff9.png>)

### Enable the HUD and logging with information property list and user defaults

Alternatively, you can enable the HUD and logging programmatically with one of the following methods:

- Add `MetalHudEnabled` to your app’s `Info.plist` file.
- Add `MetalHUDForceEnabled=1` in your app’s <doc://com.apple.documentation/documentation/Foundation/UserDefaults>.

### Utilize the logging capabilities

If you enable logging, once per second as your app runs, the HUD writes data in the following format to the console:

```
metal-HUD: <first-frame-number-integer>,<graphics-memory-usage-float>,<process-memory-usage-float>,<first-frame-present-interval-float>,<first-frame-gpu-time-float>,...<last-frame-present-interval-float>,<last-frame-gpu-time-float>
```

For example, the HUD writes the following data to the console while running the
<doc://com.apple.documentation/documentation/Metal/rendering-a-scene-with-deferred-lighting-in-swift>
sample code project:

![A screenshot of the per-frame statistics logs output from the Metal Performance HUD.](<monitoring-your-metal-apps-graphics-performance/2d0235bf65935735d131d311.png>)

When you enable shader compiler logging, as your app runs, the Metal HUD emits signposts for each compiled shader. The subsystem is `com.apple.metal.hud` and the category is `Logging`.

```
[com.apple.metal.hud:Logging] CompileShader: name: ParticleVs compilation-time: 5496250 cached: 0
[com.apple.metal.hud:Logging] CompileShader: name: ParticlePs compilation-time: 6335000 cached: 0
```

### Understand encoder GPU time tracking

You can turn on encoder GPU time tracking by ticking the `Enable Encoder GPU Time Tracking` option in the configuration panel or by setting `MTL_HUD_ENCODER_TIMING_ENABLED` to `1` in the environment variable.

With encoder GPU time tracking, the Metal Performance HUD leverages <doc://com.apple.documentation/documentation/Metal/gpu-counters-and-counter-sample-buffers> to track GPU timing for each command encoder to provide enhanced GPU time reporting.

> Important: Encoder GPU time tracking is only available if your app doesn’t use the Metal counter sample buffer. It also may increase the CPU cost of the Metal HUD due to additional data processing.

Encoder GPU time measures GPU activity by tracking the start and end times of work within individual encoder stages (vertex, fragment, and compute). This differs from standard GPU time, which captures the overall duration of command buffers. For command buffers containing many encoders, there may be idle periods in between encoders that can inflate the standard GPU time, providing a less accurate measure of actual GPU workload.

The overlay shows the encoder GPU time as well as the GPU time and the percentage to the total frame time for each encoder type. Below the timing metrics, a GPU timeline visualizes the GPU execution of the last three frames, updating every second.

![A screenshot showing the Metal HUD encoder GPU time.](<monitoring-your-metal-apps-graphics-performance/ed7d37b560b82b98e43ad534.png>)

With the encoder GPU time tracking enabled, the Metal Performance HUD also tracks command buffer and encoder labels. Two new optional metrics become available: Top Labeled Command Buffers and Top Labeled Encoders. These metrics show the three most GPU-intensive command buffers and encoders by label, helping you quickly pinpoint potential performance bottlenecks.

![A screenshot showing the top labeled command buffers and encoders.](<monitoring-your-metal-apps-graphics-performance/b1901039d9a6e2ac4bee8316.png>)

### Display the value range of metrics

You can visualize the range of common metrics in the overlay by enabling the Show Metrics Value Range option in the configuration panel or by setting `MTL_HUD_SHOW_VALUE_RANGE` to `1` in the environment variable.

With this option, the HUD visualizes common metrics in three columns:

- The first column contains the average value of the last 120 frames.
- The second column contains the minimum values of the last 1200 frames.
- The third column contains the maximum values of the last 1200 frames.

![A screenshot showing the Metal HUD reporting value range of metrics.](<monitoring-your-metal-apps-graphics-performance/9dcac597816483de3bc03505.png>)

---

Copyright &copy; 2026 Apple Inc. All rights reserved. | [Terms of Use](https://www.apple.com/legal/internet-services/terms/site.html) | [Privacy Policy](https://www.apple.com/privacy/privacy-policy)