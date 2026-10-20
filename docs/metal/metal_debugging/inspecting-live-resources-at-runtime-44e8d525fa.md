Source: [https://developer.apple.com/documentation/xcode/inspecting-live-resources-at-runtime](<https://developer.apple.com/documentation/xcode/inspecting-live-resources-at-runtime>)

<a id="inspecting-live-resources-at-runtime"></a>

# Inspecting live resources at runtime

Validate your resources by viewing the contents of your textures and buffers while debugging your Metal app.

<a id="overview"></a>

## Overview

You can preview contents of textures and buffers while debugging your app in Xcode by pausing on a breakpoint, inspecting a variable that references the resource, and then clicking the Preview button.
This is one quick way to validate that your resources have the correct contents while debugging at runtime.

> Important: If you disable GPU Frame Capture, you can’t inspect resource content while your app is running.
> See <doc://com.apple.Xcode/documentation/Xcode/Capturing-a-Metal-workload-in-Xcode> to learn how to reenable it.

<a id="inspect-your-textures-and-buffers"></a>

### Inspect your textures and buffers

First, pause the app inside a scope that contains a variable referencing the resource.
You can achieve this by setting a breakpoint on a line that references the resource.
To set a breakpoint, click the line number to the left of the source editor.
The example below shows a breakpoint for the line where `_skyMap` is bound to the render encoder:

![A screenshot of Xcode’s source editor, highlighting a line of code with a breakpoint.](<inspecting-live-resources-at-runtime/5d5ca638f1ad2581c2cede57.png>)

Then, when yor app pauses at the breakpoint, move the pointer over the variable referencing the resource to reveal the Value inspector.

![A screenshot of the source editor, breaking at a line of code with a breakpoint. The variable underscore sky map is highlighted.](<inspecting-live-resources-at-runtime/242fe7d5089b123c1d187d7e.png>)

Finally, click the Preview button to show the contents of the resource.

![A screenshot of the Preview popover showing the contents of the variable underscore sky map.](<inspecting-live-resources-at-runtime/744bde105d5eef23f81ad00c.png>)

If the resource is a texture and has multiple slices, like the sky map above, you can drag the slider at the bottom of the Preview popover to see each slice.
If the resource has any unexpected values, you can investigate further with the Metal debugger (see [Investigating visual artifacts](./investigating-visual-artifacts-caaf4d188b.md)).

---

Copyright © 2026 Apple Inc. All rights reserved. | [Terms of Use](https://www.apple.com/legal/internet-services/terms/site.html) | [Privacy Policy](https://www.apple.com/privacy/privacy-policy)
