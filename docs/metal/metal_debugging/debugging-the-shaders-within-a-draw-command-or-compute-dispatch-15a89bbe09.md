Source: [https://developer.apple.com/documentation/xcode/debugging-the-shaders-within-a-draw-command-or-compute-dispatch](<https://developer.apple.com/documentation/xcode/debugging-the-shaders-within-a-draw-command-or-compute-dispatch>)

<a id="debugging-the-shaders-within-a-draw-command-or-compute-dispatch"></a>

# Debugging the shaders within a draw command or compute dispatch

Identify and fix problematic shaders in your app using the shader debugger.

<a id="overview"></a>

## Overview

If you notice any visual artifacts while running your app, such as missing geometry or invalid pixels,
you can use the shader debugger to investigate problematic shaders.
Step through your shader source code and inspect variable values until you discover the problem.
Then, just edit the shader source and reload the shader to verify your fix.

> Important: Include source code when you capture a Metal workload because the shader debugger needs it to function correctly.
> For more information, see <doc://com.apple.Xcode/documentation/Xcode/Building-your-project-with-embedded-shader-sources>.

<a id="debug-your-shader"></a>

### Debug your shader

To begin debugging a shader, select the draw command or compute dispatch of interest in the Debug navigator. Then, click the Shader Debugger button in the
debug bar to begin debugging any of the associated shaders for the currently bound pipeline state.

![A screenshot of the Bound Resources viewer highlighting the Shader Debugger button in the debug bar.](<debugging-the-shaders-within-a-draw-command-or-compute-dispatch/9a70faa839a3af85347b97fb.png>)

The shader debugger opens a dialog that includes a tab for each shader type in use so you can easily select the shader region of interest.
For example, if your draw command has a vertex and fragment shader, the dialog includes Vertex and Fragment tabs.

The Vertex tab shows the geometry of your draw command.
You can immediately start debugging your vertex shader by clicking the Debug button on the bottom right because the shader debugger automatically selects the first vertex.

For more information, see [Inspecting the geometry of a draw command](./inspecting-the-geometry-of-a-draw-command-d5e87bd31c.md).

![A screenshot of the Region of Interest dialog with the Debug button highlighted.](<debugging-the-shaders-within-a-draw-command-or-compute-dispatch/86fa1b8ebc737a82eabedb14.png>)

The dialog includes tabs for Mesh and Object, if applicable, instead of the Vertex tab when a draw command uses a mesh-based pipeline state.

The Mesh and Object tabs show the geometry of your draw command.
You can immediately start debugging your mesh or object shaders by clicking the Debug button on the bottom right because the shader debugger automatically selects the first mesh grid and its first mesh.

![A screenshot of the Region of Interest dialog with the Debug button highlighted.](<debugging-the-shaders-within-a-draw-command-or-compute-dispatch/c36a9215b98635ed38f47fab.png>)

You can set the threadgroup position that produced a mesh in the thread selector by clicking the Mesh tab and selecting a mesh in the table or the geometry view.
You can also set the thread position that produced a vertex in a mesh by choosing Thread Position for Vertex and selecting a vertex in the table or the geometry view.
Alternatively, you can set the thread position that produced a primitive or an index in a mesh by choosing Thread Position for Primitive or Index.

![A screenshot of the Mesh tab in the Metal debugger that highlights a dialog in the lower right corner that shows the details of a specific mesh in a scene a person selects. At the top of the dialog, its Thread Position of dropdown menu is set to Vertex. The dialog’s detailed information includes fields for thread position in grid, thread position in threadgroup, and threadgroup position in grid.](<debugging-the-shaders-within-a-draw-command-or-compute-dispatch/5adf4c1ded087795ce8d9223.png>)

You can set the threadgroup position that produced a mesh grid in the thread selector by clicking the Object tab and selecting a mesh grid in the table or the geometry view.

![A screenshot of the Object tab in the Metal debugger that highlights a dialog in the lower right corner that shows the details of a specific mesh grid in a scene a person selects. The dialog’s detailed information includes fields for thread position in grid, thread position in threadgroup, and threadgroup position in grid.](<debugging-the-shaders-within-a-draw-command-or-compute-dispatch/b7bf4b9e132f77b2fdb0e149.png>)

For more information, see [Inspecting the geometry of a draw command](./inspecting-the-geometry-of-a-draw-command-d5e87bd31c.md).

The Fragment tab shows the first attachment of your draw command, and hides other attachments by default.
You can immediately start debugging your fragment shader by clicking the Debug button on the bottom right because the shader debugger automatically selects a pixel within a debuggable region.
Alternatively, you can select a different pixel, change the visible attachments, and so on.

For more information, see [Inspecting the attachments of a draw command](./inspecting-the-attachments-of-a-draw-command-4d183522b4.md).

![A screenshot of the Region of Interest dialog with the Debug button highlighted.](<debugging-the-shaders-within-a-draw-command-or-compute-dispatch/ecd35e2ec8bed2e48efb5057.png>)

If you select a compute dispatch rather than a draw command, you can immediately start debugging your compute shader by clicking the Debug button on the bottom right because the shader debugger automatically selects the first threadgroup.

![A screenshot of the Region of Interest dialog with the Debug button highlighted.](<debugging-the-shaders-within-a-draw-command-or-compute-dispatch/8ef40776b5900f18b4903880.png>)

You can also expand the Functions to Debug option to select a subset of functions within your shader source.
Using a subset of functions can dramatically decrease the amount of the shader debugger’s initial processing.

![A screenshot of the Region of Interest dialog with the Functions to Debug section expanded.](<debugging-the-shaders-within-a-draw-command-or-compute-dispatch/da7c47685a8f0685f86d7e45.png>)

You can also select a subset of functions in the Vertex, Mesh, Object, and Fragment tabs by clicking Debug while holding down the Option key.

<a id="step-through-your-shader-code"></a>

### Step through your shader code

After you click the Debug button, the shader debugger displays the shader source in the Shader editor (see [Inspecting shaders](./inspecting-shaders-27f9d3e31a.md)). The call tree on the left shows each executed line in your shader.
The values of the variables appear to the right of each shader line of source code in the Shader editor.
For example, in the screenshot below, you can see that the `in` variable has a value containing `721.5`, `815.5`, and so on.

![A screenshot of the shader debugger showing the Shader editor and the Attachments viewer side by side. On the left, the Debug navigator displays the region of interest and the call tree.](<debugging-the-shaders-within-a-draw-command-or-compute-dispatch/fb6ea868933a74f665063239.png>)

If your shader is producing incorrect results, you can examine the value of variables on each line until you see an unexpected value that indicates the cause of the problem.
Use the call tree to quickly inspect your shader:

![A screenshot of the shader debugger with an active shader debugging session. The top-level function in the call tree is selected and its corresponding line of source code in the Shader editor to the right is highlighted.](<debugging-the-shaders-within-a-draw-command-or-compute-dispatch/6c15050a831ab48b3f5ecd4c.png>)

When you select a line in the call tree, its corresponding line of source code in the Shader editor to the right appears with a green highlight.
This line is also referred to as the *location of the playhead*.
Use your keyboard arrow keys in the call tree to advance the playhead through your code one line at a time.
As you step through the call tree, the playhead follows along in the source code in the Shader editor.

| Arrow key | Stepping direction |
| --- | --- |
| Down Arrow | Steps forward |
| Up Arrow | Steps backward |
| Right Arrow | Steps in |
| Left Arrow | Steps out |

Alternatively, you can change the playhead location by clicking any line in the Shader editor, and the shader debugger moves to the corresponding function in the call tree.

![A screenshot of the shader debugger with an active shader debugging session. A line of code is selected in the call tree.](<debugging-the-shaders-within-a-draw-command-or-compute-dispatch/2ba256effd0dd1743bee6032.png>)

<a id="iterate-through-loops"></a>

### Iterate through loops

Unlike a traditional CPU debugger, the shader debugger shows the value of all variables at the same time, with no need to step to the next line.
If you decide not to use the call tree to iterate through loops, you can switch the visible loop iteration directly within the Shader editor.
Click the Loop Iteration tab on the right above the loop, just before the variables sidebar.
When you select a different iteration, the variables within the sidebar update to reflect their values during that iteration.

![A screenshot of the shader debugger with an active shader debugging session. The Loop Iteration Selection menu is open, with iteration 5 selected.](<debugging-the-shaders-within-a-draw-command-or-compute-dispatch/e81932c53497ea977f86ad67.png>)

<a id="inspect-variable-values"></a>

### Inspect variable values

To inspect the value of a variable, move the pointer over it.
For example, in the screenshot below, hovering over `linearSampler` shows the sampler properties in a popover.

![A screenshot of the value inspection popover that appears when the pointer hovers over a sampler variable.](<debugging-the-shaders-within-a-draw-command-or-compute-dispatch/aeabd5f7c6a2a64f6d10821d.png>)

Alternatively, you can toggle the Preview button in the variables sidebar to show the value inline with the source.
This is useful if you want to compare the values of multiple variables simultaneously.

![A screenshot of the inline variable inspection view.](<debugging-the-shaders-within-a-draw-command-or-compute-dispatch/7b2b6a0fa6ff302d102c6476.png>)

If a variable has nested properties, you can disclose them in a cascading fashion.

![A screenshot showing the hierarchy of a variable’s nested properties.](<debugging-the-shaders-within-a-draw-command-or-compute-dispatch/ce7ce5c6de4136fbd85fea53.png>)

This enables you to dive in to an object’s data by showing you more than the Shader editor can fit in the right sidebar.

In addition to the selected pixel or thread, the shader debugger also shows the variable values for nearby pixels, or other threads within the threadgroup, in what is known as the *region of interest*.
When you expand a variable preview, the shader debugger shows the values of variables for all pixels or threads within the region of interest.

> Tip: The region of interest appears in the Attachments viewer as a fluorescent orange square (see <doc://com.apple.Xcode/documentation/Xcode/Inspecting-the-attachments-of-a-draw-command>), and in the Geometry viewer as an orange vertex (see <doc://com.apple.Xcode/documentation/Xcode/Inspecting-the-geometry-of-a-draw-command>).

Use this rendering to visually check that the variable is the value you expect.
For graphical data, the visualization can be easier to verify than numerical data alone.
Move the pointer over a pixel or thread to see the variable value for it.
Then, you can click the pixel or thread to select it.
The Shader editor automatically changes the variables in the variables sidebar to reflect their values during the execution of the shader when using the newly selected pixel or thread.

![A screenshot of the value inspector when the pointer is hovering over a pixel.](<debugging-the-shaders-within-a-draw-command-or-compute-dispatch/9adbc5a87e5e39d4854345ee.png>)

In the preview, the mask shows the pixels or threads within the region of interest that executed the line of code.
Consider the example below, where the fragment shader branches depending on the vertex in-position.
In the mask, the pixels within the region of interest that passed the condition appear with a white color, and pixels that didn’t pass the condition appear with a black color.

![A screenshot of the inline variable inspection view.](<debugging-the-shaders-within-a-draw-command-or-compute-dispatch/de04094c0f56642d53d8da02.png>)

<a id="update-your-shader"></a>

### Update your shader

After changing a shader, you can update the captured frame with the new source code by clicking the Reload Shaders button in the debug bar.

![A screenshot of the Reload Shaders button in the debug bar.](<debugging-the-shaders-within-a-draw-command-or-compute-dispatch/b281111b8effd8c7f14eeabc.png>)

After updating the captured frame, the shader debugger does the following:

- Updates variable views to show their new values.
- Redraws attachments in the assistant editor.
- Maintains your place in the captured frame, which provides an interactive environment to enhance your shader development and debugging.

> Important: Changes to your shader source only exist within the shader debugger.
> Your original source code doesn’t change.
> If your shader results look correct after reloading the shader, make sure that you copy your changes to your original shader source code.

If your shader is producing correct results, but taking a long time to run, consider profiling your Metal workload and inspecting the shader source in the Shader editor.
For more information, see [Inspecting shaders](./inspecting-shaders-27f9d3e31a.md).

---

Copyright © 2026 Apple Inc. All rights reserved. | [Terms of Use](https://www.apple.com/legal/internet-services/terms/site.html) | [Privacy Policy](https://www.apple.com/privacy/privacy-policy)
