Source: [https://developer.apple.com/library/archive/documentation/3DDrawing/Conceptual/MTLBestPracticesGuide/FrameRate.html](<https://developer.apple.com/library/archive/documentation/3DDrawing/Conceptual/MTLBestPracticesGuide/FrameRate.html>)

<a id="//apple_ref/doc/uid/TP40016642-CH23"></a>

<a id="//apple_ref/doc/uid/TP40016642-CH23-SW1"></a>



<a id="frame-rate-ios-and-tvos"></a>

## Frame Rate (iOS and tvOS)

**Best Practice:** Present your drawables at a consistent and stable frame rate.

Most apps target a frame rate of 60 FPS, equivalent to 16.67 ms per frame. However, apps that are consistently unable to complete a frame’s work within this time should target a lower frame rate to avoid jitter.

<a id="//apple_ref/doc/uid/TP40016642-CH23-DontLinkElementID_35"></a>



Important

The minimum acceptable frame rate for real-time gaming is 30 FPS. Lower frame rates are considered a poor user experience and should be avoided. If your app cannot maintain a minimum acceptable frame rate of 30 FPS, you should consider further optimizations or decreased workloads (spending less than 33.33 ms per frame).

<a id="//apple_ref/doc/uid/TP40016642-CH23-DontLinkElementID_3"></a>



<a id="querying-and-adjusting-the-frame-rate"></a>

### Querying and Adjusting the Frame Rate

The maximum frame rate of iOS and tvOS devices can be queried through the [maximumFramesPerSecond](https://developer.apple.com/reference/uikit/uiscreen/2806814-maximumframespersecond) property. For iOS devices, this value is usually 60 FPS; for tvOS devices, this value can vary based on the hardware capabilities of an attached screen or the user-selected resolution on Apple TV.

Using an `MTKView` object is the recommended way to adjust your app’s frame rate. By default, the view renders at 60 FPS; to target a different frame rate, set the view’s `preferredFramesPerSecond` property to your desired value.

<a id="//apple_ref/doc/uid/TP40016642-CH23-DontLinkElementID_36"></a>



Note

A MetalKit view always rounds the value of `preferredFramesPerSecond` to the nearest factor of the device’s [maximumFramesPerSecond](https://developer.apple.com/reference/uikit/uiscreen/2806814-maximumframespersecond) value. If your app cannot maintain its maximum target frame rate (e.g. 60 FPS), then set this property to a lower-factor frame rate (e.g. 30 FPS). Setting the value of `preferredFramesPerSecond` to a non-factor frame rate may produce unexpected results.

Maintaining a target frame rate requires your app to completely update, encode, schedule, and execute a frame’s work during the allowed render interval time (e.g. less than 16.67ms per frame to maintain a 60 FPS frame rate).

<a id="//apple_ref/doc/uid/TP40016642-CH23-DontLinkElementID_4"></a>



<a id="adjust-the-drawable-presentation-time"></a>

### Adjust the Drawable Presentation Time

The `presentDrawable:` method registers a drawable presentation to occur as soon as possible, which is usually at the next display refresh interval *after* the drawable has been rendered or written to. If your app can maintain its maximum target frame rate, as set via the `preferredFramesPerSecond` property, then simply calling the `presentDrawable:` method is enough to maintain a consistent and stable frame rate.

If your app targets a lower-factor frame rate, the display refresh rate (e.g. 60 FPS) may fire more frequently than your app’s render loop (e.g. 30 FPS). This means that the `presentDrawable:` method could present a drawable earlier than expected if a frame is rendered before the next display refresh interval (e.g. 16.67 ms intervals).

The `presentDrawable:afterMinimumDuration:` method allows you to specify a minimum display time for each drawable, meaning that drawable presentations occur only *after* the previous drawable has spent enough time on the display. This lets you synchronize your drawable’s presentation time with your app’s render loop. The relationship between the `preferredFramesPerSecond` and `presentDrawable:afterMinimumDuration:` API is shown in Listing 8-1

<a id="//apple_ref/doc/uid/TP40016642-CH23-SW3"></a>

**Listing 8-1**Presenting drawables after a minimum display time

1. `view.preferredFramesPerSecond = 30;`
2. `/* ... */`
3. `[commandBuffer presentDrawable:view.currentDrawable afterMinimumDuration:1.0/view.preferredFramesPerSecond];`

<a id="next_previous"></a>

[Native Screen Scale (iOS and tvOS)](./NativeScreenScale-html-5c9a4a3a0a.md#//apple_ref/doc/uid/TP40016642-CH8-SW1)

[Load and Store Actions](./LoadandStoreActions-html-cd3d663642.md#//apple_ref/doc/uid/TP40016642-CH20-SW1)

Copyright © 2018 Apple Inc. All rights reserved.
[Terms of Use](http://www.apple.com/legal/terms/site.html) |
[Privacy Policy](http://www.apple.com/privacy/) |
[Updated: 2017-03-27](https://developer.apple.com/library/archive/documentation/3DDrawing/Conceptual/MTLBestPracticesGuide/RevisionHistory.html#//apple_ref/doc/uid/TP40016642-CH99-DontLinkElementID_50)
