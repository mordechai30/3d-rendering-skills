Source: [https://developer.apple.com/documentation/xcode/inspecting-acceleration-structures](<https://developer.apple.com/documentation/xcode/inspecting-acceleration-structures>)

<a id="inspecting-acceleration-structures"></a>

# Inspecting acceleration structures

Reveal ray intersection bottlenecks by examining your acceleration structures.

<a id="overview"></a>

## Overview

An *acceleration structure* is a data structure that Metal uses to accelerate ray intersection tests on the GPU.
The Metal debugger allows you to inspect an acceleration structure with the Acceleration Structure viewer.
After opening an acceleration structure, you can view it and its associated properties, along with various highlights.

<a id="navigate-your-acceleration-structure"></a>

### Navigate your acceleration structure

You can navigate your acceleration structure using the two panes of the Acceleration Structure viewer — the structure outline on the left or the scene view on the right.

![A screenshot of the Acceleration Structure viewer, which consists of a navigator, a scene view, and a control bar.](<inspecting-acceleration-structures/8e97b7f950ca2ca3e45f27c0.png>)

The structure outline shows the components of your acceleration structure, along with their various properties.
You can click any row in the structure outline to highlight the component of your acceleration structure in the scene view, or Control-click to jump to it.

The scene view shows a 3D representation of your acceleration structure.
You can navigate around the scene or interact with your acceleration structure using the following controls:

| Action | Result |
| --- | --- |
| W (or ↑) | Zooms in at the viewport center |
| A (or ←) | Pans left |
| S (or ↓) | Zooms out at the viewport center |
| D (or →) | Pans right |
| Up Arrow/Down Arrow | Pans up/Pans down |
| Option-Up Arrow/Down Arrow | Zooms in/Zooms out on the pointer |
| Drag | Rotates the camera |
| Control-click | Performs the selection, depending on the selection mode |
| Shift-Control-click | Selects a primitive acceleration structure |
| Option-Control-click | Selects the geometry |
| Option-Command-Control-click | Selects a primitive |
| Command-Control-click | Selects an instance |

<a id="change-the-camera-mode"></a>

### Change the camera mode

If you’re using the Fly camera, dragging in the scene view rotates the camera.
Alternatively, when using the Orbit camera, dragging orbits the camera around any primitive beneath the pointer, or around the scene center if there’s no primitive.
You can click the Camera button in the control bar to switch between modes.

![A screenshot of the Camera button in the control bar.](<inspecting-acceleration-structures/c697a9d421cdd938c47ae3ba.png>)

<a id="configure-intersection-functions"></a>

### Configure intersection functions

Xcode automatically picks an intersection function table to use when rendering the scene, depending on how you open your acceleration structure.
For example, if you open your acceleration structure from the Bound Resources viewer, Xcode selects any bound intersection function tables with matching intersector tags. For more information, see [Inspecting the bound resources for a command](./inspecting-the-bound-resources-for-a-command-9e627795a0.md).
If you open your acceleration structure from the All Resources viewer or the Memory viewer, Xcode automatically selects the last intersection function table, with matching intersector tags, in your workload. For more information, see [Analyzing memory usage](./analyzing-memory-usage-7042e7d9aa.md).

You can switch to the intersection function table outline to configure which intersection function table the Acceleration Structure viewer uses.
If you select None, the Acceleration Structure viewer doesn’t use any intersection functions and relies solely on the geometry intersection.
If you select an intersection function table, the system uses the intersection function corresponding to the intersection function table offset of each geometry to evaluate whether to accept an intersection. For more information, see <doc://com.apple.documentation/documentation/Metal/MTLAccelerationStructureGeometryDescriptor/intersectionFunctionTableOffset> and `accept_intersection` in the [Metal Shading Language Specification](inspecting-acceleration-structures/41538b30d2f1140a5b2a0c84.pdf).

![A screenshot of the intersection function table outline. The sphere intersection function is selected, and the matching geometries are highlighted in the scene view.](<inspecting-acceleration-structures/89121de8e5fd362709c1294a.png>)

<a id="configure-acceleration-structure-traversal-behavior"></a>

### Configure acceleration structure traversal behavior

You can override the default behavior of the acceleration structure traversal by clicking the arrow in the bottom right of the control bar.
The popover options let you configure the same properties as the intersector to control traversal behavior (see [Metal Shading Language Specification](inspecting-acceleration-structures/41538b30d2f1140a5b2a0c84.pdf)).
Match the traversal behavior with your shader to ensure that the Acceleration Structure viewer is correct.

![A screenshot of the Intersector Options popover.](<inspecting-acceleration-structures/d0f9421642d4fa1aeda6532c.png>)

<a id="view-your-acceleration-structure-with-highlights"></a>

### View your acceleration structure with highlights

You can view your acceleration structure with different highlights to emphasize various properties.
To enable and switch between modes, click the Highlight button in the control bar.

![A screenshot of the Highlight button in the control bar.](<inspecting-acceleration-structures/d65e10d6e75e13223901eda7.png>)

- Bounding Volume Traversals:
  You can use the Bounding Volume Traversals mode to highlight areas of your scene that are more expensive to traverse.
  Xcode color-codes the number of traversals it takes to intersect your acceleration structure on a scale from white (fewer traversals) to dark blue (more traversals).
  As you move the pointer around the viewport, the inspector (at the bottom left) updates several traversal statistics for the pixel under the pointer, along with the corresponding minimum and maximum values in the viewport.

![A screenshot of the Acceleration Structure viewer displaying the scene with the Bounding Volume Traversals highlight mode.](<inspecting-acceleration-structures/4763e1bf6a0836e950a06b2d.png>)

- All Node Traversal:
  You can use the All Node Traversal mode to highlight the expensive parts of your scene that may be occluded.  
  Xcode uses the same color-coding as the Bounding Volume Traversals highlight, but doesn’t stop traversing when it hits a surface.
  In the example below, you can see the eyes inside the ninja’s head:

![A screenshot of the Acceleration Structure viewer displaying the scene with the All Node Traversal highlight mode.](<inspecting-acceleration-structures/53e6b55c15bd91680c51164a.png>)

- Acceleration Structures:
  This mode highlights different primitive acceleration structures.
  The inspector shows the primitive acceleration structure index as you move the pointer around the viewport.

![A screenshot of the Acceleration Structure viewer displaying the scene with the Acceleration Structures highlight mode.](<inspecting-acceleration-structures/697a51ca5158c33d5aaeebf8.png>)

- Geometries:
  This mode highlights different geometries within primitive acceleration structures.
  The inspector shows the `geometry_id` attribute as you move the pointer around the viewport. For more information, see [Metal Shading Language Specification](inspecting-acceleration-structures/41538b30d2f1140a5b2a0c84.pdf).

![A screenshot of the Acceleration Structure viewer displaying the scene with the Geometries highlight mode.](<inspecting-acceleration-structures/d0cc728eff604fd734d03b11.png>)

- Primitives:
  This mode highlights different primitives within primitive acceleration structures.
  The inspector shows the `geometry_id` and `primitive_id` attributes as you move the pointer around the viewport. For more information, see [Metal Shading Language Specification](inspecting-acceleration-structures/41538b30d2f1140a5b2a0c84.pdf).

![A screenshot of the Acceleration Structure viewer displaying the scene with the Primitives highlight mode.](<inspecting-acceleration-structures/727eec0408d5dd9e2d086501.png>)

- Instances:
  This mode highlights different instances of primitive acceleration structures.
  The inspector shows the `instance_id` attribute as you move the pointer around the viewport. For more information, see [Metal Shading Language Specification](inspecting-acceleration-structures/41538b30d2f1140a5b2a0c84.pdf).

![A screenshot of the Acceleration Structure viewer displaying the scene with the Instances highlight mode.](<inspecting-acceleration-structures/2bdcf2580b28e75ac4e2ba50.png>)

- Intersection Functions:
  This mode highlights different intersection functions. 
  The inspector shows the intersection function index as you move the pointer around the viewport.

![A screenshot of the Acceleration Structure viewer displaying the scene with the Intersection Functions highlight mode.](<inspecting-acceleration-structures/18c82d7fb07fdceb3ab88698.png>)

<a id="view-per-primitive-data"></a>

### View per-primitive data

To view per-primitive data, first navigate to a primitive in the structure outline.
Then, click the arrow next to the data property to open a Buffer viewer containing the per-primitive data.

![A screenshot of the per-primitive data popover in the instance acceleration structure.](<inspecting-acceleration-structures/395ac877984181d7d822b591.png>)

For information on configuring the Buffer viewer to better interpret the data, see [Inspecting buffers](./inspecting-buffers-1a497a63cf.md).

> Tip: You can use Option-Command-Control-click at any time in the scene view to quickly reveal the primitive in the structure outline.

<a id="view-motion-data"></a>

### View motion data

If your acceleration structure includes motion data, Xcode automatically shows additional motion data properties per-instance or per-geometry in the structure outline.

![A screenshot of the Acceleration Structure viewer highlighting the motion data properties for one instance in the instance acceleration structure.](<inspecting-acceleration-structures/3e2f94ddf1570260a896a3a3.png>)

Additional motion controls appear in the control bar.
You can drag the motion timeline playhead to change the preview time.
Alternatively, you can click the Play/Pause button and Xcode repeatedly bounces the current motion time between the minimum start time and the maximum end time.

![A screen recording of the Acceleration Structure viewer visualizing an instance motion acceleration structure. It repeatedly bounces the current motion time between the minimum start time and the maximum end time.](<inspecting-acceleration-structures/556c9297c315116dbcaa0d41.gif>)

---

Copyright © 2026 Apple Inc. All rights reserved. | [Terms of Use](https://www.apple.com/legal/internet-services/terms/site.html) | [Privacy Policy](https://www.apple.com/privacy/privacy-policy)
