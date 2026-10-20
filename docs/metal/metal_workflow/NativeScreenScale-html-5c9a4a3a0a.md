Source: [https://developer.apple.com/library/archive/documentation/3DDrawing/Conceptual/MTLBestPracticesGuide/NativeScreenScale.html](<https://developer.apple.com/library/archive/documentation/3DDrawing/Conceptual/MTLBestPracticesGuide/NativeScreenScale.html>)

<a id="//apple_ref/doc/uid/TP40016642-CH8"></a>

<a id="//apple_ref/doc/uid/TP40016642-CH8-SW1"></a>



<a id="native-screen-scale-ios-and-tvos"></a>

## Native Screen Scale (iOS and tvOS)

**Best Practice:** Render drawables at the exact pixel size of your target display.

The pixel size of your drawables should always match the exact pixel size of their target display. This is critical to avoid rendering to off-screen pixels or incurring an additional sampling stage.

The `UIScreen` class provides two properties that define the native size and scale factor of a physical screen: `nativeBounds` and `nativeScale`. Query the `nativeBounds` property to determine the native bounding rectangle of the screen, in pixels. Query the `nativeScale` property to determine the native scale factor used to convert points to pixels.

<a id="//apple_ref/doc/uid/TP40016642-CH8-DontLinkElementID_41"></a>



Important

In iOS and tvOS, most drawing technologies measure size in points instead of pixels. Your Metal app should always measure size in pixels and avoid points altogether. To learn more about the difference between these two units, see [Points Versus Pixels](https://developer.apple.com/library/archive/documentation/2DDrawing/Conceptual/DrawingPrintingiOS/GraphicsDrawingOverview/GraphicsDrawingOverview.html#//apple_ref/doc/uid/TP40010156-CH14-SW7).

<a id="//apple_ref/doc/uid/TP40016642-CH8-DontLinkElementID_11"></a>



<a id="use-a-metalkit-view-to-support-native-screen-scale"></a>

### Use a MetalKit View to Support Native Screen Scale

The `MTKView` class automatically supports native screen scale. By default, the size of the view’s current drawable is always guaranteed to match the size of the view itself.

<a id="//apple_ref/doc/uid/TP40016642-CH8-DontLinkElementID_42"></a>



Note

If you create your own `UIView` subclass that is backed by a `CAMetalLayer` object, you must first set the view’s `contentScaleFactor` property to match the screen’s `nativeScale` property. Next, make sure you adjust the size of your render targets whenever your view’s size changes. Finally, adjust the layer’s `drawableSize` property to match the native screen scale. For an example of how to match the native screen scale, see the *MetalBasic3D* sample.

<a id="next_previous"></a>

[Drawables](./Drawables-html-a6bbc21e80.md#//apple_ref/doc/uid/TP40016642-CH2-SW1)

[Frame Rate (iOS and tvOS)](./FrameRate-html-5b14b85210.md#//apple_ref/doc/uid/TP40016642-CH23-SW1)

Copyright © 2018 Apple Inc. All rights reserved.
[Terms of Use](http://www.apple.com/legal/terms/site.html) |
[Privacy Policy](http://www.apple.com/privacy/) |
[Updated: 2017-03-27](https://developer.apple.com/library/archive/documentation/3DDrawing/Conceptual/MTLBestPracticesGuide/RevisionHistory.html#//apple_ref/doc/uid/TP40016642-CH99-DontLinkElementID_50)
