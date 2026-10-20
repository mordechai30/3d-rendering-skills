Source: [https://developer.apple.com/documentation/xcode/inspecting-sampler-states](<https://developer.apple.com/documentation/xcode/inspecting-sampler-states>)

<!--
{
  "documentType" : "article",
  "framework" : "Xcode",
  "identifier" : "/documentation/Xcode/Inspecting-sampler-states",
  "metadataVersion" : "0.1.0",
  "role" : "article",
  "title" : "Inspecting sampler states"
}
-->

# Inspecting sampler states

Verify your sampler state configurations by examining their properties.

## Overview

The Metal debugger allows you to inspect a sampler state with the Sampler State viewer.
After opening a sampler state, you can view its associated properties and preview the sampling behavior.
For more information, see [Inspecting the bound resources for a command](/documentation/Xcode/Inspecting-the-bound-resources-for-a-command) or [Analyzing memory usage](/documentation/Xcode/Analyzing-memory-usage).

### Navigate your sampler state

The Sampler State viewer shows the properties of your sampler state on the left (as configured by <doc://com.apple.documentation/documentation/Metal/MTLSamplerDescriptor>) and a preview on the right. The preview illustrates how pixels in a texture appear when using your sampler state.

![A screenshot of the Sampler State viewer displaying a sampler state configured with nearest filtering and clamp-to-edge address mode.](<inspecting-sampler-states/b7de4bb2306eb8554d867df5.png>)

The square region in the center of the preview corresponds to UV coordinates within the range of `0.0` to `1.0`.

![A screenshot of the Sampler State viewer displaying a sampler state configured with nearest filtering and clamp-to-edge address mode. The region in bounds is highlighted.](<inspecting-sampler-states/cf98fcd4045b48c6655576b8.png>)

You can use the preview to quickly verify the configuration for your sampler state.
For example, if you want a texture to mirror, but it’s drawing a constant value instead, you can check the sampler state.
In the screenshot below, the sampler state is configured to clamp to a border color that’s opaque black, rather than using mirror repeat as the address mode:

![A screenshot of the Sampler State viewer displaying a sampler state configured with nearest filtering and clamp-to-border address mode. The border color is opaque black.](<inspecting-sampler-states/be3169ea1b98a3f91a126b32.png>)

### Try various combinations

The properties you configure when creating a sampler state determine how a texture looks when sampling it.
The properties related to filtering control how pixels combine when the sample footprint is either larger or smaller than a pixel, or when it’s between mipmap levels.
The address mode determines the texture coordinate at each pixel when a read falls outside the bounds of a texture. You can try using different combinations of filtering
and addressing modes until you achieve your desired look.

|Properties                                                                                                                                                                                                                                                                  |Preview                                                                                                                                                                                                                                           |
|----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
|<doc://com.apple.documentation/documentation/Metal/MTLSamplerMinMagFilter/nearest>, <doc://com.apple.documentation/documentation/Metal/MTLSamplerAddressMode/clampToEdge>                                                                                                   |![A screenshot of the Sampler State viewer displaying a sampler state configured with nearest filtering and clamp-to-edge address mode.](<inspecting-sampler-states/be7db40112b23f02c843eafb.png>)                                                            |
|<doc://com.apple.documentation/documentation/Metal/MTLSamplerMinMagFilter/nearest>, <doc://com.apple.documentation/documentation/Metal/MTLSamplerAddressMode/mirrorClampToEdge>                                                                                             |![A screenshot of the Sampler State viewer displaying a sampler state configured with nearest filtering and mirror-clamp-to-edge address mode.](<inspecting-sampler-states/c21b25cce3084e39a6d1093c.png>)                                              |
|<doc://com.apple.documentation/documentation/Metal/MTLSamplerMinMagFilter/nearest>, <doc://com.apple.documentation/documentation/Metal/MTLSamplerAddressMode/repeat>                                                                                                        |![A screenshot of the Sampler State viewer displaying a sampler state configured with nearest filtering and repeat address mode.](<inspecting-sampler-states/04e06db87c535d212f13a425.png>)                                                                  |
|<doc://com.apple.documentation/documentation/Metal/MTLSamplerMinMagFilter/nearest>, <doc://com.apple.documentation/documentation/Metal/MTLSamplerAddressMode/mirrorRepeat>                                                                                                  |![A screenshot of the Sampler State viewer displaying a sampler state configured with nearest filtering and mirror-repeat address mode.](<inspecting-sampler-states/ec2631f593b8f9de10d66cb5.png>)                                                           |
|<doc://com.apple.documentation/documentation/Metal/MTLSamplerMinMagFilter/nearest>, <doc://com.apple.documentation/documentation/Metal/MTLSamplerAddressMode/clampToZero>                                                                                                   |![A screenshot of the Sampler State viewer displaying a sampler state configured with nearest filtering and clamp-to-zero address mode.](<inspecting-sampler-states/439df61de937b5680e372be4.png>)                                                             |
|<doc://com.apple.documentation/documentation/Metal/MTLSamplerMinMagFilter/nearest>, <doc://com.apple.documentation/documentation/Metal/MTLSamplerAddressMode/clampToBorderColor>, <doc://com.apple.documentation/documentation/Metal/MTLSamplerBorderColor/opaqueBlack>     |![A screenshot of the Sampler State viewer displaying a sampler state configured with nearest filtering and clamp-to-border address mode. The border color is opaque black.](<inspecting-sampler-states/439df61de937b5680e372be4.png>)           |
|<doc://com.apple.documentation/documentation/Metal/MTLSamplerMinMagFilter/nearest>, <doc://com.apple.documentation/documentation/Metal/MTLSamplerAddressMode/clampToBorderColor>, <doc://com.apple.documentation/documentation/Metal/MTLSamplerBorderColor/opaqueWhite>     |![A screenshot of the Sampler State viewer displaying a sampler state configured with nearest filtering and clamp-to-border address mode. The border color is opaque white.](<inspecting-sampler-states/703f5a6097b9534471b84618.png>)           |
|<doc://com.apple.documentation/documentation/Metal/MTLSamplerMinMagFilter/nearest>, <doc://com.apple.documentation/documentation/Metal/MTLSamplerAddressMode/clampToBorderColor>, <doc://com.apple.documentation/documentation/Metal/MTLSamplerBorderColor/transparentBlack>|![A screenshot of the Sampler State viewer displaying a sampler state configured with nearest filtering and clamp-to-border address mode. The border color is transparent black.](<inspecting-sampler-states/5781868fd144008abed87019.png>)|
|<doc://com.apple.documentation/documentation/Metal/MTLSamplerMinMagFilter/linear>, <doc://com.apple.documentation/documentation/Metal/MTLSamplerAddressMode/clampToEdge>                                                                                                    |![A screenshot of the Sampler State viewer displaying a sampler state configured with linear filtering and clamp-to-edge address mode.](<inspecting-sampler-states/af3519e822c8e038c18a089a.png>)                                                              |
|<doc://com.apple.documentation/documentation/Metal/MTLSamplerMinMagFilter/linear>, <doc://com.apple.documentation/documentation/Metal/MTLSamplerAddressMode/clampToEdge>                                                                                                    |![A screenshot of the Sampler State viewer displaying a sampler state configured with linear filtering and mirror-clamp-to-edge address mode.](<inspecting-sampler-states/1197c776a6ac2dbb8726fc7b.png>)                                                |
|<doc://com.apple.documentation/documentation/Metal/MTLSamplerMinMagFilter/linear>, <doc://com.apple.documentation/documentation/Metal/MTLSamplerAddressMode/repeat>                                                                                                         |![A screenshot of the Sampler State viewer displaying a sampler state configured with linear filtering and repeat address mode.](<inspecting-sampler-states/24aefd2a2aee0cc6ff241f54.png>)                                                                    |
|<doc://com.apple.documentation/documentation/Metal/MTLSamplerMinMagFilter/linear>, <doc://com.apple.documentation/documentation/Metal/MTLSamplerAddressMode/mirrorRepeat>                                                                                                   |![A screenshot of the Sampler State viewer displaying a sampler state configured with linear filtering and mirror-repeat address mode.](<inspecting-sampler-states/87d3731acad2c44b9d2258f8.png>)                                                             |
|<doc://com.apple.documentation/documentation/Metal/MTLSamplerMinMagFilter/linear>, <doc://com.apple.documentation/documentation/Metal/MTLSamplerAddressMode/clampToZero>                                                                                                    |![A screenshot of the Sampler State viewer displaying a sampler state configured with linear filtering and clamp-to-zero address mode.](<inspecting-sampler-states/c9538e0ae40ff7359fc70c28.png>)                                                               |
|<doc://com.apple.documentation/documentation/Metal/MTLSamplerMinMagFilter/linear>, <doc://com.apple.documentation/documentation/Metal/MTLSamplerAddressMode/clampToBorderColor>, <doc://com.apple.documentation/documentation/Metal/MTLSamplerBorderColor/opaqueBlack>      |![A screenshot of the Sampler State viewer displaying a sampler state configured with linear filtering and clamp-to-border address mode. The border color is opaque black.](<inspecting-sampler-states/c9538e0ae40ff7359fc70c28.png>)             |
|<doc://com.apple.documentation/documentation/Metal/MTLSamplerMinMagFilter/linear>, <doc://com.apple.documentation/documentation/Metal/MTLSamplerAddressMode/clampToBorderColor>, <doc://com.apple.documentation/documentation/Metal/MTLSamplerBorderColor/opaqueWhite>      |![A screenshot of the Sampler State viewer displaying a sampler state configured with linear filtering and clamp-to-border address mode. The border color is opaque white.](<inspecting-sampler-states/9f23e074f55b2027210e1462.png>)             |
|<doc://com.apple.documentation/documentation/Metal/MTLSamplerMinMagFilter/linear>, <doc://com.apple.documentation/documentation/Metal/MTLSamplerAddressMode/clampToBorderColor>, <doc://com.apple.documentation/documentation/Metal/MTLSamplerBorderColor/transparentBlack> |![A screenshot of the Sampler State viewer displaying a sampler state configured with linear filtering and clamp-to-border address mode. The border color is transparent black.](<inspecting-sampler-states/798b242fb5638f8da3d486a1.png>)  |

---

Copyright &copy; 2026 Apple Inc. All rights reserved. | [Terms of Use](https://www.apple.com/legal/internet-services/terms/site.html) | [Privacy Policy](https://www.apple.com/privacy/privacy-policy)