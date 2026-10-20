Source: [https://developer.apple.com/documentation/xcode/inspecting-textures](<https://developer.apple.com/documentation/xcode/inspecting-textures>)

<a id="inspecting-textures"></a>

# Inspecting textures

Discover issues in your textures by examining their content.

<a id="overview"></a>

## Overview

The Metal debugger allows you to view the contents of a texture in the Texture viewer.
First, flip the texture to the correct orientation and adjust the colors to ensure accuracy.
Then, check for pixel issues like infinite values, not-a-number values, or any values that exceed the current EDR headroom of your display.
Hover over pixels within the texture to inspect their values, then find any anomalies by selecting a pixel and comparing it with others.
Finally, compare across mipmap levels to check for visual issues.
For more information, see [Inspecting the bound resources for a command](./inspecting-the-bound-resources-for-a-command-9e627795a0.md) or [Analyzing memory usage](./analyzing-memory-usage-7042e7d9aa.md).

<a id="navigate-your-texture"></a>

### Navigate your texture

The Texture viewer contains several controls for interacting with and displaying your texture.
If your texture contains multiple slices, such as <doc://com.apple.documentation/documentation/Metal/MTLTextureType/type2DArray>, the controls in the title bar are disabled until you click a texture image.
The active texture image has a system accent color border.

![A screenshot of the Texture viewer, which consists of a title bar, a canvas, and a control bar. It shows a texture with three slices, with the first texture slice selected.](<inspecting-textures/8a4d59be5e4a1c699c08d4e4.png>)

Groups of texture slices that contain related content, such as the faces for a texture of type <doc://com.apple.documentation/documentation/Metal/MTLTextureType/typeCube>, are part of the same texture image.

<a id="flip-your-texture"></a>

### Flip your texture

If your renderer is using a different coordinate system and your texture image is upside down or flipped horizontally, you can flip it to the correct orientation in the Texture viewer.
Click the texture actions button, then choose Flip Horizontally or Flip Vertically.
Xcode flips groups of related texture slices, such as cubemaps, as a whole, and it flips unrelated texture slices independently.

![A screenshot of the actions menu. The Flip Horizontally menu item is highlighted.](<inspecting-textures/0002eb970db40018f41c5884.png>)

<a id="configure-texture-rendering"></a>

### Configure texture rendering

Xcode automatically configures the color properties based on your texture, but you can configure them manually by clicking the Colors button in the title bar.
You configure texture rendering on a per-texture-image basis. Follow these guidelines:

- Set the color space to the one that the device display uses.
  For example, use sRGB if you’re debugging an iPhone workload.
- If you’re using a display that supports extended dynamic range, you can enable the Extended Dynamic Range Content option to render the texture with extended range.
  When this option is enabled, Xcode draws hatching on any pixels containing values above your display EDR headroom.
  Consider lowering the brightness of your display to increase the available headroom.
- Xcode shows additional controls to manually configure rendering if you select Default (No color-match) as the color space.
  You can then configure the range of visible colors, channel swizzling, and whether the alpha is premultiplied.

![A screenshot of the Texture Image Color Options popover. It consists of controls for color space, tone mapping, and color sizzling.](<inspecting-textures/a27c08e195b3eb278310aeb7.png>)

<a id="view-texture-properties"></a>

### View texture properties

You can view properties for the active texture image, such as width and height, by clicking the Info button in the title bar.

![A screenshot of the Texture Image Properties popover.](<inspecting-textures/05a9b6e3005a2a9aac686ae3.png>)

<a id="view-texture-issues"></a>

### View texture issues

The Issues button in the title bar becomes active if your texture contains any pixels (or samples) with values that are infinite, are not-a-number, or exceed the current EDR headroom of your display.

You can click the Issues button to see more information, and then click the Jump button to focus on a pixel (or sample) causing the issue.

![A screenshot of the Issues popover indicating that there are pixels exceeding the display EDR headroom. There’s a button next to the message for jumping to one such pixel.](<inspecting-textures/a99556f8b9f28082e14407e6.png>)

<a id="inspect-select-and-compare-pixel-values"></a>

### Inspect, select, and compare pixel values

Move the pointer over a pixel (or a sample if your texture is of type <doc://com.apple.documentation/documentation/Metal/MTLTextureType/type2DMultisample> or <doc://com.apple.documentation/documentation/Metal/MTLTextureType/type2DMultisampleArray>) to inspect its value.

![A screenshot of the value inspector when the pointer is hovering over pixel 2077, 919.](<inspecting-textures/5799f8e0c553f29196178f7f.png>)

Then, you can select the pixel by clicking it.
Alternatively, you can click and hold so that Xcode selects the pixel, zooms in, and immediately opens the value inspector.

You can also select a pixel using the coordinate input controls on the right of the control bar.
Type in the coordinates for the pixel you want, such as `X: 100` and `Y: 100`.
Depending on your texture configuration, Xcode may show additional controls.

![A screenshot of the control bar highlighting the coordinate input controls.](<inspecting-textures/dbe8116d1a6fe02d4460390e.png>)

Click the Jump button in the control bar to zoom in to the selected pixel or sample.
Xcode automatically focuses when you click the stepper to the right of each text field.

![A screenshot of the control bar highlighting the Jump button.](<inspecting-textures/a5813d509dd785d259904831.png>)

You can also move the pointer over a different pixel (or sample) to compare the values.
If the selected pixel is to the left of the pixel beneath the pointer, the values of the selected pixel appear on the left of the inspector.
If it’s to the right, the values appear on the right.
Xcode highlights the coordinates for the selected pixel in the inspector to show which values correspond to which pixel.

![A screenshot of the value inspector comparing the pixel values beneath the pointer and at the selection. The pointer is hovering over pixel 2080, 919, and the selection is at pixel 2094, 919.](<inspecting-textures/a8637194c78f3165d5ef6d5a.png>)

If you open multiple Attachments viewers or Texture viewers, you can compare pixels across different textures.
For information on configuring editors within your Xcode workspace, see <doc://com.apple.documentation/documentation/Xcode/configuring-the-xcode-project-window>.

<a id="compare-mipmap-levels"></a>

### Compare mipmap levels

By default, the Texture viewer shows all of your texture’s mipmap levels side by side.
However, if you want to visually compare different mipmap levels, you can enable stacking.
Click the texture actions button, and then choose Stack Mips.

![A screenshot of the Texture viewer showing a mipmapped cubemap texture. The actions menu is open and the Stack Mips menu item is highlighted.](<inspecting-textures/3d889f27690a59a7abce50b0.png>)

Drag the slice slider in the control bar to visually compare different mipmap levels.

![A screen recording of the Texture viewer visualizing the different mipmap levels of a texture as the user moves the pointer along the slider.](<inspecting-textures/6a8c7ccc4fa20b99d60af359.gif>)

> Note: By default, the Texture viewer stacks 3D textures, such as <doc://com.apple.documentation/documentation/Metal/MTLTextureType/type3D>, using the z-coordinate.
> You can disable stacking to see the depth slices side by side.
> If your 3D texture has multiple mipmap levels, you can choose either Stack Mips or Stack Z.

---

Copyright © 2026 Apple Inc. All rights reserved. | [Terms of Use](https://www.apple.com/legal/internet-services/terms/site.html) | [Privacy Policy](https://www.apple.com/privacy/privacy-policy)
