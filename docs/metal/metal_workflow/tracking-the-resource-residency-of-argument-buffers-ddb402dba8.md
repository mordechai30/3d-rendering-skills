Source: [https://developer.apple.com/documentation/metal/tracking-the-resource-residency-of-argument-buffers?language=objc](<https://developer.apple.com/documentation/metal/tracking-the-resource-residency-of-argument-buffers?language=objc>)

<a id="tracking-the-resource-residency-of-argument-buffers"></a>

# Tracking the resource residency of argument buffers

Optimize resource performance within an argument buffer.

<a id="discussion"></a>

## Discussion

The Metal driver can’t automatically track the residency of argument buffer resources, but you can track it manually.

<a id="track-argument-buffer-resource-residency-manually"></a>

### Track argument buffer resource residency manually

Call an [`MTLRenderCommandEncoder`](https://developer.apple.com/documentation/Metal/MTLRenderCommandEncoder) or [`MTLComputeCommandEncoder`](https://developer.apple.com/documentation/Metal/MTLComputeCommandEncoder) method:

- For individual resources, call [`useResource(_:usage:stages:)`](https://developer.apple.com/documentation/Metal/MTLRenderCommandEncoder/useResource(_:usage:stages:)) or [`useResource(_:usage:)`](https://developer.apple.com/documentation/Metal/MTLComputeCommandEncoder/useResource(_:usage:)).
- For all resources in a heap, call [`useHeap(_:stages:)`](https://developer.apple.com/documentation/Metal/MTLRenderCommandEncoder/useHeap(_:stages:)) or [`useHeap(_:)`](https://developer.apple.com/documentation/Metal/MTLComputeCommandEncoder/useHeap(_:)).

These methods perform two important functions:

- They add argument buffer resources to the set of resources that the render or compute pass needs resident.
- They ensure that argument buffer resources are in a format that’s compatible with the required function operation, as an [`MTLResourceUsage`](https://developer.apple.com/documentation/Metal/MTLResourceUsage) value specifies.

The methods with a `stages` parameter also insert dependency hazards, similar to [`MTLFence`](https://developer.apple.com/documentation/Metal/MTLFence) instances for that stage.

Call these methods before issuing any draw or dispatch calls that may access the specified resources.

> Note:
> To track resource access and dependency hazards, use `doc://com.apple.metal/documentation/Metal/MTLFence` instances.
>
> If all the required resources aren’t resident when executing a render or compute pass, the associated `doc://com.apple.metal/documentation/Metal/MTLCommandBuffer` instance fails.

---

Copyright © 2026 Apple Inc. All rights reserved. | [Terms of Use](https://www.apple.com/legal/internet-services/terms/site.html) | [Privacy Policy](https://www.apple.com/privacy/privacy-policy)
