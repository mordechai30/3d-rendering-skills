Source: [https://developer.apple.com/documentation/xcode/capturing-a-metal-workload-in-xcode](<https://developer.apple.com/documentation/xcode/capturing-a-metal-workload-in-xcode>)

<!--
{
  "documentType" : "article",
  "framework" : "Xcode",
  "identifier" : "/documentation/Xcode/Capturing-a-Metal-workload-in-Xcode",
  "metadataVersion" : "0.1.0",
  "role" : "article",
  "title" : "Capturing a Metal workload in Xcode"
}
-->

# Capturing a Metal workload in Xcode

Analyze your app’s performance by configuring your project to use the Metal debugger.

## Overview

You can use Xcode to capture your app’s Metal workload. First, ensure that the GPU Frame Capture option is enabled in the runtime diagnostics options. Then, when your app is running, click the Metal Capture button in the debug bar, select a scope, and click Capture.

### Configure the GPU Frame Capture options

Xcode automatically enables the GPU Frame Capture option if your target links to the <doc://com.apple.documentation/documentation/Metal> framework, or any other framework that uses the Metal API. If you’re collaborating on a project, it’s possible that someone else may have disabled GPU Frame Capture. To ensure it’s enabled, follow these steps:

1. In the Xcode toolbar, choose Edit Scheme from the Scheme menu.
   ![An Xcode screenshot showing the Scheme menu with the Edit Scheme menu item highlighted.](<capturing-a-metal-workload-in-xcode/5261feab15a253d198e797cc.png>)
2. Select the Run scheme action.
3. Select the Options tab.
4. Choose a GPU Frame Capture option and click Close.
   ![A screenshot of the Xcode scheme editor highlighting the GPU Frame Capture option.](<capturing-a-metal-workload-in-xcode/47c620f4c6cb662de6d87a92.png>)

The GPU Frame Capture options include the following:

- Automatically: Captures Metal or OpenGL ES API usage in your app.
  If your target doesn’t link to the Metal framework or the OpenGL ES framework, the Metal Capture button doesn’t appear in the debug bar. If your app uses both the Metal  API and the OpenGL ES API, you can click and hold the Capture GPU Frame icon to choose which API usage to capture.
- Metal: Captures only Metal API usage in your app.
  If your app doesn’t use the Metal API, Xcode disables the Metal Capture button in the debug bar.
- Disabled: Doesn’t capture Metal usage in your app. GPU Frame Capture has a tiny, but measurable, effect on your app’s CPU processing time, so choose this option when you want to test your app’s maximum performance level.

### Capture your Metal workload while debugging

While debugging your app, you can capture a GPU trace by following these steps:

1. Click the Metal Capture button in the debug bar.
   ![A screenshot of the Metal Capture popover, accessible from the Metal Capture button in the debug bar.](<capturing-a-metal-workload-in-xcode/b6cca0c6886175583df55afe.png>)
2. Select the scope that you want to capture. This can be a frame, Metal layer, command queue, device, or any custom scopes that you set up previously. For more information, see [Creating and using custom capture scopes](/documentation/Xcode/Creating-and-using-custom-capture-scopes).
3. Select the count. Depending on the scope, this might include the number of frames or command buffers.
4. Click Capture.

Xcode automatically starts capturing a GPU trace when the scope starts, then finishes the capture based on the scope and count you select.
To manually stop the capture, you can click the Finish button at any time.

### Capture your Metal workload after deployment

Capture a GPU trace after deploying your app by following these steps:

1. In Xcode, choose Debug > Debug Executable.
2. Select your app in Finder and click Choose. Xcode automatically brings up the scheme editor.
3. Click the Options tab, choose a GPU Frame Capture option, and click Close.
   ![A screenshot of the Xcode scheme editor highlighting the GPU Frame Capture option.](<capturing-a-metal-workload-in-xcode/f9d8ff81928a79a84c8210a3.png>)
4. Run your app by choosing Product > Run.
5. Click the Metal Capture button in the debug bar.
   ![An Xcode screenshot of the Metal Capture popover, accessible from the Metal Capture button in the debug bar.](<capturing-a-metal-workload-in-xcode/bdab938dbeeee23d570d5719.png>)
6. Select the scope and count that you want to capture.
7. Click Capture.

Xcode automatically starts capturing a GPU trace when the scope starts, then finishes the capture based on the count you select.
To manually stop the capture, you can click the Finish button at any time.

### Configure advanced capture options

The Metal Capture popover includes an Advanced section with additional options for controlling capture behavior. To reveal these options, click Show next to Advanced in the popover.

![A screenshot of the Metal Capture popover with the Advanced section expanded, showing additional capture options.](<capturing-a-metal-workload-in-xcode/31a5c7445b633b9adc1e4d57.png>)

The advanced capture options include the following:

- Keyboard shortcut: Choose a keyboard shortcut to start a capture while your app is in the foreground. This option is only available on macOS.
- Profile after replay: Automatically profile your captured workload with default settings after Xcode finishes replaying it. Profiling has an initial performance impact on the Metal debugger, so only enable this option when debugging your app’s performance. You can always profile later as needed.
- Include MetalFX temporal scaler history: Record historical data for MetalFX temporal scalers to improve captured texture quality during replay. Enabling this option can make captures slower. This option is available when your app uses MetalFX temporal scaling.
- Optimize shared memory capture: Control how Xcode optimizes capturing CPU writes to resources using shared memory storage, which can improve capture performance and reduce the GPU trace’s size on disk.
  - **Automatic**: Xcode enables the optimization when Xcode can determine that the environment supports it safely, and disables it when system call interposition is unavailable.
  - **Always**: Force the optimization on regardless of environment. Use this when you have large or slow GPU frame captures and know your app doesn’t write to shared-memory buffers via system calls.
  - **Never**: Disable the optimization entirely. Use this if you suspect the optimization is producing incorrect results.

### Save the capture to your computer

To save your captured Metal workload as a GPU trace, choose File > Export. For more information on replaying GPU trace files, see [Replaying a GPU trace file](/documentation/Xcode/Replaying-a-GPU-trace-file).

---

Copyright &copy; 2026 Apple Inc. All rights reserved. | [Terms of Use](https://www.apple.com/legal/internet-services/terms/site.html) | [Privacy Policy](https://www.apple.com/privacy/privacy-policy)