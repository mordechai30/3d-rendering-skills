Source: [https://developer.apple.com/library/archive/documentation/3DDrawing/Conceptual/MTLBestPracticesGuide/Drawables.html](<https://developer.apple.com/library/archive/documentation/3DDrawing/Conceptual/MTLBestPracticesGuide/Drawables.html>)

<a id="//apple_ref/doc/uid/TP40016642-CH2"></a>

<a id="//apple_ref/doc/uid/TP40016642-CH2-SW1"></a>



<a id="//apple_ref/doc/uid/TP40016642-CH7"></a>

<a id="//apple_ref/doc/uid/TP40016642-CH7-DontLinkElementID_31"></a>



<a id="drawables"></a>

## Drawables

**Best Practice:** Hold a drawable as briefly as possible.

Most Metal apps implement a layer-backed view defined by a `CAMetalLayer` object. This layer vends an efficient displayable resource conforming to the `CAMetalDrawable` protocol, commonly referred to as a *drawable*. A drawable provides a `MTLTexture` object that is typically used as a displayable render target attached to a `MTLRenderPassDescriptor` object, with the goal of being presented on the screen.

A drawable’s presentation is registered by calling a command buffer’s `presentDrawable:` method before calling its `commit` method. However, the drawable itself is actually presented only after the command buffer has completed execution and the drawable has been rendered or written to.

A drawable tracks whether it has outstanding render or write requests on it and will not present until those requests have been completed. A command buffer registers its drawable requests only when it is scheduled for execution. Registering a drawable presentation after the command buffer is scheduled guarantees that all command buffer work will be completed before the drawable is actually presented. Do not wait for the command buffer to complete its GPU work before registering a drawable presentation; this will cause a considerable CPU stall.

<a id="//apple_ref/doc/uid/TP40016642-CH2-DontLinkElementID_32"></a>



Important

To avoid presenting a drawable before any work is scheduled, or to avoid holding on to a drawable longer than necessary, call a command buffer’s `presentDrawable:` method instead of a drawable’s `present` method. `presentDrawable:` is a convenience method that calls the given drawable's `present` method via the command buffer's `addScheduledHandler:` callback.

<a id="//apple_ref/doc/uid/TP40016642-CH2-DontLinkElementID_1"></a>



<a id="hold-a-drawable-as-briefly-as-possible"></a>

### Hold a Drawable as Briefly as Possible

Drawables are expensive system resources created and maintained by the Core Animation framework. They exist within a limited and reusable resource pool and may or may not be available when requested by your app. If there is no drawable available at the time of your request, the calling thread is blocked until a new drawable becomes available (which is usually at the next display refresh interval).

To hold a drawable as briefly as possible, follow these two steps:

1. Always acquire a drawable as late as possible; preferably, immediately before encoding an on-screen render pass. A frame’s CPU work may include dynamic data updates and off-screen render passes that you can perform before acquiring a drawable.
2. Always release a drawable as soon as possible; preferably, immediately after finalizing a frame’s CPU work. It is highly advisable to contain your rendering loop within an autorelease pool block to avoid possible deadlock situations with multiple drawables.

   <a id="//apple_ref/doc/uid/TP40016642-CH2-DontLinkElementID_33"></a>



   Note

   As of iOS 10 and tvOS 10, drawables can be safely held for post-presentation property queries, such as `drawableID` and `presentedTime`. Otherwise, drawables should be released when they are no longer needed, which is usually after a call to a command buffer’s `presentDrawable:` method.

Figure 6-1 shows the lifetime of a drawable in relation to other CPU work.

<a id="//apple_ref/doc/uid/TP40016642-CH2-SW2"></a>

**Figure 6-1**The lifetime of a drawable
![image: ../Art/DisplayManagement_DrawableLifetime_2x.png](<Drawableshtml/f672a86c343ba74da8b32ed3.png>)

<a id="//apple_ref/doc/uid/TP40016642-CH2-DontLinkElementID_2"></a>



<a id="use-a-metalkit-view-to-interact-with-drawables"></a>

### Use a MetalKit View to Interact with Drawables

Using an `MTKView` object is the preferred way to interact with drawables. An `MTKView` object is backed by a `CAMetalLayer` object and provides the `currentDrawable` property to acquire the drawable for the current frame. The current frame renders into this drawable and the `presentDrawable:` method schedules the actual presentation to occur at the next display refresh interval. The `currentDrawable` property is automatically updated at the end of every frame.

An `MTKView` object also provides the `currentRenderPassDescriptor` convenience property that references the current drawable’s texture; use this property to create a render command encoder that renders into the current drawable. A call to the `currentRenderPassDescriptor` property implicitly acquires the drawable for the current frame, which is then stored in the `currentDrawable` property.

<a id="//apple_ref/doc/uid/TP40016642-CH2-DontLinkElementID_34"></a>



Note

If you create your own `UIView` or `NSView` subclass that is backed by a `CAMetalLayer` object, you must explicitly acquire a drawable and use its texture to configure a render pass descriptor. You can also do this for your own `MTKView` object, but it is much easier to simply use the `currentRenderPassDescriptor` convenience property. For an example of how to acquire a drawable from a `UIView` or `NSView` subclass, see the *MetalBasic3D* sample.

Listing 6-1 shows how to use a drawable with a MetalKit view.

<a id="//apple_ref/doc/uid/TP40016642-CH2-SW3"></a>

**Listing 6-1**Using drawables with a MetalKit view

1. `- (void)render:(MTKView *)view {`
2. `// Update your dynamic data`
3. `[self update];`
5. `// Create a new command buffer`
6. `id <MTLCommandBuffer> commandBuffer = [_commandQueue commandBuffer];`
8. `// BEGIN encoding any off-screen render passes`
9. `/* ... */`
10. `// END encoding any off-screen render passes`
12. `// BEGIN encoding your on-screen render pass`
13. `// Acquire a render pass descriptor generated from the drawable's texture`
14. `// 'currentRenderPassDescriptor' implicitly acquires the drawable`
15. `MTLRenderPassDescriptor* renderPassDescriptor = view.currentRenderPassDescriptor;`
17. `// If there's a valid render pass descriptor, use it to render into the current drawable`
18. `if(renderPassDescriptor != nil) {`
19. `id<MTLRenderCommandEncoder> renderCommandEncoder = [commandBuffer renderCommandEncoderWithDescriptor:renderPassDescriptor];`
20. `/* Set render state and resources */`
21. `/* Issue draw calls */`
22. `[renderCommandEncoder endEncoding];`
23. `// END encoding your on-screen render pass`
25. `// Register the drawable presentation`
26. `[commandBuffer presentDrawable:view.currentDrawable];`
27. `}`
29. `/* Register optional callbacks */`
30. `// Finalize the CPU work and commit the command buffer to the GPU`
31. `[commandBuffer commit];`
32. `}`
34. `- (void)drawInMTKView:(MTKView *)view {`
35. `@autoreleasepool {`
36. `[self render:view];`
37. `}`
38. `}`

<a id="next_previous"></a>

[Buffer Bindings](./BufferBindings-html-052b8dacc4.md#//apple_ref/doc/uid/TP40016642-CH28-SW3)

[Native Screen Scale (iOS and tvOS)](./NativeScreenScale-html-5c9a4a3a0a.md#//apple_ref/doc/uid/TP40016642-CH8-SW1)

Copyright © 2018 Apple Inc. All rights reserved.
[Terms of Use](http://www.apple.com/legal/terms/site.html) |
[Privacy Policy](http://www.apple.com/privacy/) |
[Updated: 2017-03-27](https://developer.apple.com/library/archive/documentation/3DDrawing/Conceptual/MTLBestPracticesGuide/RevisionHistory.html#//apple_ref/doc/uid/TP40016642-CH99-DontLinkElementID_50)
