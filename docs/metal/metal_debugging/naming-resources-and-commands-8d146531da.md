Source: [https://developer.apple.com/documentation/xcode/naming-resources-and-commands](<https://developer.apple.com/documentation/xcode/naming-resources-and-commands>)

<a id="naming-resources-and-commands"></a>

# Naming resources and commands

Enhance the debugging of your Metal app using labels and grouping.

<a id="overview"></a>

## Overview

Resource labels and command debug groups are useful when debugging and profiling your app using Metal tools.
Assigning meaningful resource labels helps you find your specific resources more quickly.
Logically grouping commands lets you easily navigate the workload after capturing it.

> Note: The properties and methods described here don’t affect the graphics-rendering or compute-processing behavior of your app.

<a id="annotate-resources"></a>

### Annotate resources

Many Metal objects provide a <doc://com.apple.documentation/documentation/Metal/MTLResource/label> property where you can assign a meaningful string.
These labels appear in each Metal tool, allowing you to easily identify specific objects.

In addition, for <doc://com.apple.documentation/documentation/Metal/MTLBuffer>, the <doc://com.apple.documentation/documentation/Metal/MTLBuffer/addDebugMarker(_:range:)> method allows you to mark and identify specific data ranges.
You can call the <doc://com.apple.documentation/documentation/Metal/MTLBuffer/removeAllDebugMarkers()> method to clear the existing markers.

<a id="annotate-commands"></a>

### Annotate commands

Command buffers and command encoders provide the following methods for you to easily identify specific groups of Metal commands in your app:

- On an <doc://com.apple.documentation/documentation/Metal/MTLCommandBuffer> object, call <doc://com.apple.documentation/documentation/Metal/MTLCommandBuffer/pushDebugGroup(_:)> and <doc://com.apple.documentation/documentation/Metal/MTLCommandBuffer/popDebugGroup()> to group commands within that buffer.
- On an <doc://com.apple.documentation/documentation/Metal/MTLCommandEncoder> object, call <doc://com.apple.documentation/documentation/Metal/MTLCommandEncoder/pushDebugGroup(_:)> and <doc://com.apple.documentation/documentation/Metal/MTLCommandEncoder/popDebugGroup()> to group commands within that encoder. In addition, call <doc://com.apple.documentation/documentation/Metal/MTLCommandEncoder/insertDebugSignpost(_:)> to mark interesting locations in the encoder.

Xcode pushes and pops debug groups using unique stacks that exist only within the lifetime of their associated <doc://com.apple.documentation/documentation/Metal/MTLCommandBuffer> or <doc://com.apple.documentation/documentation/Metal/MTLCommandEncoder>.
You can nest debug groups by pushing multiple groups onto the stack before popping previous groups.

Use these methods to simplify your app development process, particularly for tasks that involve many Metal commands per buffer or encoder.

The following example demonstrates pushing and popping multiple debug groups:

```swift
func encodeRenderPass(commandBuffer: MTLCommandBuffer, descriptor: MTLRenderPassDescriptor) { 
    guard let renderEncoder = commandBuffer.makeRenderCommandEncoder(descriptor: descriptor) else { return }
    renderEncoder.label = "My Render Encoder"
    renderEncoder.pushDebugGroup("My Render Pass")

        renderEncoder.pushDebugGroup("Pipeline Setup")
        // Render pipeline commands.
        renderEncoder.popDebugGroup() // Pops "Pipeline Setup".

        renderEncoder.pushDebugGroup("Vertex Setup")
        // Vertex function commands.
        renderEncoder.popDebugGroup() // Pops "Vertex Setup".

        renderEncoder.pushDebugGroup("Fragment Setup")
        // Fragment function commands.
        renderEncoder.popDebugGroup() // Pops "Fragment Setup".

        renderEncoder.pushDebugGroup("Draw Calls")
        // Drawing commands.
        renderEncoder.popDebugGroup() // Pops "Draw Calls".

    renderEncoder.popDebugGroup() // Pops "My Render Pass".
    renderEncoder.endEncoding()
}
```

The following screenshot shows how the debug groups appear in Xcode’s Debug navigator after you capture a frame:

![A screenshot of Xcode’s Debug navigator showing nested debug groups inside a render pass.](<naming-resources-and-commands/46dbc262f172e852123e6db3.png>)

---

Copyright © 2026 Apple Inc. All rights reserved. | [Terms of Use](https://www.apple.com/legal/internet-services/terms/site.html) | [Privacy Policy](https://www.apple.com/privacy/privacy-policy)
