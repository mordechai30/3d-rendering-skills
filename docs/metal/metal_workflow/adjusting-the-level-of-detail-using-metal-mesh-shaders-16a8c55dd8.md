Source: [https://developer.apple.com/documentation/metal/adjusting-the-level-of-detail-using-metal-mesh-shaders?language=objc](<https://developer.apple.com/documentation/metal/adjusting-the-level-of-detail-using-metal-mesh-shaders?language=objc>)

<a id="adjusting-the-level-of-detail-using-metal-mesh-shaders"></a>

# Adjusting the level of detail using Metal mesh shaders

Choose and render meshes with several levels of detail using object and mesh shaders.

<a id="discussion-note-this-sample-code-project-is-associated-with-wwdc22-session-10162-transform-your-geometry-with-metal-mesh-shaders"></a>

## Discussion> Note: This sample code project is associated with WWDC22 session [10162: Transform your geometry with Metal mesh shaders](https://developer.apple.com/wwdc22/10162/).

<a id="configure-the-sample-code-project"></a>

### Configure the sample code project

To run this sample, you need Xcode 14 or later, and a physical device that supports [`MTLGPUFamily.mac2`](https://developer.apple.com/documentation/Metal/MTLGPUFamily/mac2) or [`MTLGPUFamily.apple7`](https://developer.apple.com/documentation/Metal/MTLGPUFamily/apple7), such as:

- A Mac running macOS 13 or later
- An iOS device with an A15 chip or later running iOS 16 or later

This sample can only run on a physical device because it uses mesh shader features, which Simulator doesn’t support.

---

Copyright © 2026 Apple Inc. All rights reserved. | [Terms of Use](https://www.apple.com/legal/internet-services/terms/site.html) | [Privacy Policy](https://www.apple.com/privacy/privacy-policy)
