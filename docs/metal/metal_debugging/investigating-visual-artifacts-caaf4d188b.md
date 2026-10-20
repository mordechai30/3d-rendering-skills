Source: [https://developer.apple.com/documentation/xcode/investigating-visual-artifacts](<https://developer.apple.com/documentation/xcode/investigating-visual-artifacts>)

<a id="investigating-visual-artifacts"></a>

# Investigating visual artifacts

Discover, diagnose, and fix visual artifacts in your app with the Metal debugger.

<a id="overview"></a>

## Overview

If you notice any visual artifacts while running your app, you can use the Metal debugger to find and investigate problematic pixels.
First, configure your build to include shader source code (see [Building your project with embedded shader sources](./building-your-project-with-embedded-shader-sources-ef9cf22fd2.md)).
Then, take a frame capture of your app when you notice the visual artifact that you want to debug (see [Capturing a Metal workload in Xcode](./capturing-a-metal-workload-in-xcode-2364f9433b.md)).

After you have a frame capture, use the Debug navigator to find the draw command that contains the visual artifact, and use the Attachments viewer to find the pixel with the issue.
Debug the pixel to launch the shader debugger, then step through your shader source code and inspect variable values until you discover the problem.
Then, edit the shader source and reload the shader to verify your fix.

<a id="skim-through-render-attachments-in-the-debug-navigator"></a>

### Skim through render attachments in the Debug navigator

In the Metal debugger, navigate to a draw command that has the issue.
As you move your pointer over rows in the Debug navigator on the left, the Metal debugger shows a preview of the first attachment.
You can use this to quickly find any draw commands that warrant further inspection.

![A screenshot of Xcode’s Debug navigator showing the popover that appears when the pointer hovers over any command in the list.](<investigating-visual-artifacts/d8db2c7a37ead71b320ef0da.png>)

You also can filter the navigator to show only markers and commands so it’s easier to compare draw commands.

![A screenshot of Xcode’s Debug navigator highlighting the button to show only markers and commands.](<investigating-visual-artifacts/97b0ff551f33dbcc176dfc6d.png>)

When you find the problematic draw command, click it to select it.
The Metal debugger automatically shows your attachments in the assistant editor on the right.

![A screenshot of the Metal debugger showing the Bound Resources viewer and the Attachments viewer side by side for a draw command.](<investigating-visual-artifacts/77083625e535737952764b18.png>)

<a id="inspect-attachments-for-a-draw-command"></a>

### Inspect attachments for a draw command

Use the Attachments viewer to find any problematic pixels.
You can scroll to zoom in, and drag to pan.
For more information on the Attachments viewer, see [Inspecting the attachments of a draw command](./inspecting-the-attachments-of-a-draw-command-4d183522b4.md).

![A screenshot of the Metal debugger showing the Attachments viewer with the value inspector when the pointer is hovering over pixel 721, 815. The Debug button is highlighted.](<investigating-visual-artifacts/c6f52d6a1c6c5ae42e181487.png>)

Click the problematic pixel to select it, and then click the Debug button.

If the problematic pixel isn’t inside a debuggable region, it has a nongreen selection indicator (as with the blue indicator in the screenshot below). This means that the draw command didn’t write to that pixel and, therefore, you can’t debug it.
Because the Attachments viewer remembers your zoom and position, you can quickly step through different draw commands in the Debug navigator to find the right one.

![A screenshot of the Metal debugger’s Attachments viewer where the selected pixel falls outside the debuggable region for a draw command.](<investigating-visual-artifacts/5fcde292c7510491cd21b692.png>)

<a id="debug-your-fragment-shader"></a>

### Debug your fragment shader

The shader debugger displays the shader source in the Shader editor (see [Inspecting shaders](./inspecting-shaders-27f9d3e31a.md)).
The call tree on the left shows each executed line in your shader.
The values of the variables appear to the right of each shader line in the shader source code.
For example, in the screenshot below, you can see that the `in` variable has a value containing `721.5`, `815.5`, and so forth.

![A screenshot of the Metal debugger showing the Shader editor and the Attachments viewer side by side. The Debug navigator displays the region of interest and the call tree.](<investigating-visual-artifacts/fb6ea868933a74f665063239.png>)

Step through your shader source code and inspect variable values until you discover the problem.
Make changes to the shader source code, and then click the Reload Shaders button in the debug bar to refresh the variable values, along with the attachments.

![A screenshot of the Reload Shaders button in the debug bar.](<investigating-visual-artifacts/b281111b8effd8c7f14eeabc.png>)

If you still see visual artifacts, continue editing the shader and reloading it as needed until you solve the problem.

> Important: Changes to your shader source code exist only within the Metal debugger.
> Your original shader source code doesn’t change.  
> If your shader results look correct after reloading the shader, make sure that you copy your changes to your original shader source code.

To learn more, see [Debugging the shaders within a draw command or compute dispatch](./debugging-the-shaders-within-a-draw-command-or-compute-dispatch-15a89bbe09.md).

---

Copyright © 2026 Apple Inc. All rights reserved. | [Terms of Use](https://www.apple.com/legal/internet-services/terms/site.html) | [Privacy Policy](https://www.apple.com/privacy/privacy-policy)
