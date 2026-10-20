Source: [https://developer.apple.com/documentation/xcode/inspecting-the-attachments-of-a-draw-command](<https://developer.apple.com/documentation/xcode/inspecting-the-attachments-of-a-draw-command>)

<a id="inspecting-the-attachments-of-a-draw-command"></a>

# Inspecting the attachments of a draw command

Discover attachment issues by inspecting individual pixels and samples.

<a id="overview"></a>

## Overview

The Metal debugger allows you to view the contents of render attachments with the Attachments viewer.
You can inspect individual pixels (or samples) and debug them with the shader debugger.
For more information, see [Inspecting the bound resources for a command](./inspecting-the-bound-resources-for-a-command-9e627795a0.md).

<a id="inspect-your-attachments"></a>

### Inspect your attachments

The Attachments viewer contains several controls you can use to interact with and display your attachments.
Each visible attachment has its own viewer and title bar, which contains attachment-specific controls.
The control bar at the bottom of the Attachments viewer contains controls that operate on all of the attachments simultaneously.

![A screenshot of the Attachments viewer.](<inspecting-the-attachments-of-a-draw-command/163be9fe894abe31fc27cf4c.png>)

<a id="flip-your-attachments"></a>

### Flip your attachments

If your renderer is using a different coordinate system and your attachment is upside down or flipped horizontally, you can flip it to the correct orientation in the Attachments viewer.
Click the attachment actions button, then choose Flip Horizontally or Flip Vertically.

![A screenshot of the actions menu for an attachment. The Flip Horizontally menu item is highlighted.](<inspecting-the-attachments-of-a-draw-command/9e570921a516edf6c23855f7.png>)

<a id="configure-visible-attachments"></a>

### Configure visible attachments

You can configure visible attachments using the preview controls on the left of the control bar.
To hide or show an attachment, move your pointer over the attachment preview and click to toggle its visibility.

Xcode updates the previews for the hidden attachments too, so you can see at a glance whether they contain anything interesting.

![A screenshot of the control to show and hide attachments.](<inspecting-the-attachments-of-a-draw-command/eaff2420d82d1049783f4ced.png>)

<a id="toggle-overlay-visibility"></a>

### Toggle overlay visibility

To hide overlays, such as the fluorescent green outline, click the attachment and then click a selected overlay to deselect it.

![A screenshot of the context menu for an attachment. The outline overlay option is enabled and highlighted.](<inspecting-the-attachments-of-a-draw-command/f1e4bc313333096d4d94d41a.png>)

<a id="configure-attachment-rendering"></a>

### Configure attachment rendering

Xcode automatically configures the color properties based on your encoder and attachment, but you can configure them manually by clicking the Colors button in the attachment-specific controls. Follow these guidelines:

- Use the same color space that you use for rendering.
  Xcode automatically configures it to the <doc://com.apple.documentation/documentation/QuartzCore/CAMetalLayer/colorspace> property that your app sets on the <doc://com.apple.documentation/documentation/QuartzCore/CAMetalLayer>.
  If you don’t set this property, configure the color space in the Attachments viewer to the one that the device display uses.  
  For example, use sRGB if you’re debugging an iPhone workload.
- If you’re using a display that supports extended dynamic range, you can enable the Extended Dynamic Range Content option to render the attachment with extended range.
  When this option is enabled, Xcode draws hatching on any pixels containing values above your display EDR headroom.
  Lower the brightness of your display to increase the available headroom.
- Xcode shows additional controls to manually configure rendering if you select Default (No color-match) as the color space.
  You can then configure the range of visible colors, channel swizzling, and whether the alpha is premultiplied.

![A screenshot of the Texture Image Color Options popover. It consists of controls for color space, tone mapping, and color sizzling.](<inspecting-the-attachments-of-a-draw-command/96023e0db92eea230025176d.png>)

<a id="view-attachment-properties"></a>

### View attachment properties

You can view properties for an attachment, such as texture width and height, by clicking the Info button in the attachment-specific controls.

![A screenshot of the Texture Image Properties popover.](<inspecting-the-attachments-of-a-draw-command/6b33a4ba63baff5666a14287.png>)

<a id="view-attachment-issues"></a>

### View attachment issues

The Issues button in the attachment-specific controls becomes active if your attachment contains any pixels (or samples) with values that are infinite, are not-a-number, or exceed the current EDR headroom of your display.
For example, if you accidently divide by `0` in your fragment shader, Xcode draws hatching on any incorrect pixels (or samples).

You can click the Issues button to see more information, and then click the Jump button to focus on a pixel (or sample) causing the issue.

![A screenshot of the Issues popover showing that there are pixels exceeding the display EDR headroom. A button appears next to the message for jumping to one such pixel.](<inspecting-the-attachments-of-a-draw-command/55acb00029edd33ffebc8e0b.png>)

<a id="inspect-pixel-values"></a>

### Inspect pixel values

Move the pointer over a pixel or sample to inspect its value.

![A screenshot of the value inspector when the pointer is hovering over a pixel.](<inspecting-the-attachments-of-a-draw-command/49028d633dac3fc3c8703fef.png>)

<a id="inspect-select-and-compare-pixel-values"></a>

### Inspect, select, and compare pixel values

Move the pointer over a pixel (or sample if your render pass does multisample antialiasing) to inspect its value.

Then, you can select the pixel by clicking it.
Alternatively, you can click and hold so that Xcode selects the pixel, zooms in, and immediately opens the value inspector.

You can also select a pixel using the coordinate input controls on the right of the control bar.
Type in the coordinates for the pixel you want, such as `X: 100` and `Y: 100`.
Depending on your texture configuration, Xcode may show additional controls, such as the sample index.

![A screenshot of the control bar highlighting the coordinate input controls.](<inspecting-the-attachments-of-a-draw-command/dbe8116d1a6fe02d4460390e.png>)

If the selected pixel is inside a debuggable region, the coordinates are highlighted in green (see “Debug a pixel” below).
If the selected pixel is outside of such a region, Xcode highlights it using your system accent color instead.

Click the Jump button in the control bar to zoom in to the selected pixel or sample.
Xcode automatically focuses when you click the stepper to the right of each text field.

![A screenshot of the control bar highlighting the Jump button.](<inspecting-the-attachments-of-a-draw-command/a5813d509dd785d259904831.png>)

You can also move the pointer over a different pixel (or sample) to compare the values.
If the selected pixel is to the left of the pixel beneath the pointer, the values of the selected pixel appear on the left of the inspector.
If it’s to the right, the values appear on the right.
Xcode highlights the coordinates for the selected pixel in the inspector to show which values correspond to which pixel.

If you open multiple Attachment viewers or Texture viewers, you can compare pixels across different textures.
For more information, see [Inspecting textures](./inspecting-textures-c658959867.md).
For more information on configuring editors within your Xcode workspace, see <doc://com.apple.documentation/documentation/Xcode/configuring-the-xcode-project-window>.

![A screenshot of the value inspector comparing the pixel values beneath the pointer and at the selection. The pointer is hovering over pixel 1221, 1030, and the selection is at pixel 1229, 1030.](<inspecting-the-attachments-of-a-draw-command/912f80a79b01efef3800ccfc.png>)

<a id="debug-a-pixel"></a>

### Debug a pixel

Xcode outlines any regions affected by the current draw command with a fluorescent green overlay.
If you notice pixels (or samples) with unexpected values inside these regions, select them and then click the Debug button on the right of the control bar to begin debugging the fragment shader.
Xcode automatically opens your fragment shader source code with detailed thread execution history for the pixel.
For more information on debugging shaders, see [Debugging the shaders within a draw command or compute dispatch](./debugging-the-shaders-within-a-draw-command-or-compute-dispatch-15a89bbe09.md).

![A screenshot of the Attachments viewer. The Debug button in the control bar is highlighted.](<inspecting-the-attachments-of-a-draw-command/3eb544acb6b9e2b1e8f862fd.png>)

---

Copyright © 2026 Apple Inc. All rights reserved. | [Terms of Use](https://www.apple.com/legal/internet-services/terms/site.html) | [Privacy Policy](https://www.apple.com/privacy/privacy-policy)
