Source: [https://developer.apple.com/documentation/metal/using-system-tone-mapping-on-video-content?language=objc](<https://developer.apple.com/documentation/metal/using-system-tone-mapping-on-video-content?language=objc>)

<a id="using-system-tone-mapping-on-video-content"></a>

# Using system tone mapping on video content

Use EDR metadata to apply the default system tone mapping to a layer.

<a id="discussion"></a>

## Discussion

When processing video content, you usually want to work in a linear color space. You also want to display content that’s consistent with how playback would appear in AVFoundation or other playback mechanisms. To create content in your app that is consistent with the system behavior, create a Metal layer with a linear color space and attach an <doc://com.apple.documentation/documentation/QuartzCore/CAEDRMetadata> object defining how the system should tone map the video content.

The code below creates a Metal layer with an extended linear BT.2020 color space and metadata that applies an HDR10 tone mapping based on the reference display.

```objective-c
CAMetalLayer *metalLayer = [CAMetalLayer new];
metalLayer.wantsExtendedDynamicRangeContent = YES;
metalLayer.pixelFormat = MTLPixelFormatRGBA16Float;

const CFStringRef name = kCGColorSpaceExtendedLinearITUR_2020;
CGColorSpaceRef colorspace = CGColorSpaceCreateWithName(name);
metalLayer.colorspace = colorspace;

CGColorSpaceRelease(colorspace);
CAEDRMetadata *edrMetaData = [CAEDRMetadata HDR10MetadataWithMinLuminance: 0.005 maxLuminance: 1000 opticalOutputScale: 100];
metalLayer.EDRMetadata = edrMetaData;
```

Your rendering code needs to generate pixel values consistent with the EDR metadata object. For example, in the above code, the `opticalOutputScale` was set to `100`, so a pixel value of `1.0` corresponds to `100` nits. For more information, see <doc://com.apple.documentation/documentation/QuartzCore/CAEDRMetadata>.

---

Copyright © 2026 Apple Inc. All rights reserved. | [Terms of Use](https://www.apple.com/legal/internet-services/terms/site.html) | [Privacy Policy](https://www.apple.com/privacy/privacy-policy)
