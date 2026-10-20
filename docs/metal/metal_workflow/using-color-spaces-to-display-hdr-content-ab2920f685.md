Source: [https://developer.apple.com/documentation/metal/using-color-spaces-to-display-hdr-content?language=objc](<https://developer.apple.com/documentation/metal/using-color-spaces-to-display-hdr-content?language=objc>)

<a id="using-color-spaces-to-display-hdr-content"></a>

# Using color spaces to display HDR content

Use a color space when you don’t need to edit or process the pixel data.

<a id="discussion"></a>

## Discussion

If you aren’t editing the content in a linear color space, and simply need to display the content with the correct transfer function, use a color space that includes that transfer function. Create a Metal layer and set its <doc://com.apple.documentation/documentation/QuartzCore/CAMetalLayer/wantsExtendedDynamicRangeContent> property to <doc://com.apple.documentation/documentation/Swift/true>. Set the color space that matches the color primaries and transfer function of your content. The code below creates a Metal layer for content in the BT.2020 color space using the PQ transfer function:

```objective-c
CAMetalLayer *metalLayer = [CAMetalLayer new];
metalLayer.wantsExtendedDynamicRangeContent = YES;
metalLayer.pixelFormat = MTLPixelFormatBGR10A2Unorm;
const CFStringRef name = kCGColorSpaceITUR_2100_PQ;
CGColorSpaceRef colorspace = CGColorSpaceCreateWithName(name);
metalLayer.colorspace = colorspace;
CGColorSpaceRelease(colorspace);
```

---

Copyright © 2026 Apple Inc. All rights reserved. | [Terms of Use](https://www.apple.com/legal/internet-services/terms/site.html) | [Privacy Policy](https://www.apple.com/privacy/privacy-policy)
