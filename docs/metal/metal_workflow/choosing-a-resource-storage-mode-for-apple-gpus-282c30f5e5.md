Source: [https://developer.apple.com/documentation/metal/choosing-a-resource-storage-mode-for-apple-gpus?language=objc](<https://developer.apple.com/documentation/metal/choosing-a-resource-storage-mode-for-apple-gpus?language=objc>)

<a id="choosing-a-resource-storage-mode-for-apple-gpus"></a>

# Choosing a resource storage mode for Apple GPUs

Select an appropriate storage mode for your textures and buffers on Apple GPUs.

<a id="discussion"></a>

## Discussion

Apple GPUs have a unified memory model in which the CPU and the GPU share system memory. However, CPU and GPU access to that memory depends on the storage mode you choose for your resources. The [`MTLStorageMode.shared`](https://developer.apple.com/documentation/Metal/MTLStorageMode/shared) mode defines system memory that both the CPU and the GPU can access. The [`MTLStorageMode.private`](https://developer.apple.com/documentation/Metal/MTLStorageMode/private) mode defines system memory that only the GPU can access.

The [`MTLStorageMode.memoryless`](https://developer.apple.com/documentation/Metal/MTLStorageMode/memoryless) mode defines tile memory within the GPU that only the GPU can access. Tile memory has higher bandwidth, lower latency, and consumes less power than system memory.

![A diagram that shows the three types of Apple GPU resource storage modes: shared at the top, private in the middle, and memoryless at the bottom. The shared mode resource is in between a GPU and CPU with bidirectional arrows pointing to and from each. The private mode resource is next to a GPU with a bidirectional arrow between them. The memoryless mode resource appears inside a GPU’s tiled memory region.](<choosing-a-resource-storage-mode-for-apple-gpus/b57fc5b6116ea7b13d9e1a3d.png>)

<a id="choose-a-resource-storage-mode-for-buffers-or-textures"></a>

### Choose a resource storage mode for buffers or textures

The storage mode you choose depends on how you plan to use Metal resources:

- Populate and update on the CPU: Data shared by the CPU and GPU. Use [`MTLStorageMode.shared`](https://developer.apple.com/documentation/Metal/MTLStorageMode/shared). The CPU and GPU share data. This is the default for buffer and texture storage.
- Access exclusively on the GPU: Data owned by the GPU. Use [`MTLStorageMode.private`](https://developer.apple.com/documentation/Metal/MTLStorageMode/private). Choose the mode if you populate your resource with the GPU through a compute, render, or blit pass. This case is common for render targets, intermediary resources, or texture streaming. For guidance on how to copy data to a private resource, see [Copying data to a private resource](./copying-data-to-a-private-resource-638918c8f6.md).
- Populate on CPU and access frequently on GPU: Shared integrated memory for the CPU and GPU. Use [`MTLStorageMode.shared`](https://developer.apple.com/documentation/Metal/MTLStorageMode/shared).
- Temporary texture contents for GPU passes: Memory held by the GPU for textures within or between passes. Use [`MTLStorageMode.memoryless`](https://developer.apple.com/documentation/Metal/MTLStorageMode/memoryless). Memoryless mode only works for textures, and stores temporary resources in tiled memory for high performance. An example is a depth or stencil texture thatʼs used only within a single pass and isnʼt needed in an earlier or later rendering stage.

For information on setting storage modes in your app, see [Setting resource storage modes](https://developer.apple.com/documentation/Metal/setting-resource-storage-modes).

<a id="create-a-memoryless-render-target"></a>

### Create a memoryless render target

To create a memoryless render target, set the [`storageMode`](https://developer.apple.com/documentation/Metal/MTLTextureDescriptor/storageMode) property of an [`MTLTextureDescriptor`](https://developer.apple.com/documentation/Metal/MTLTextureDescriptor) to [`MTLStorageMode.memoryless`](https://developer.apple.com/documentation/Metal/MTLStorageMode/memoryless) and use this descriptor to create a new [`MTLTexture`](https://developer.apple.com/documentation/Metal/MTLTexture). Then set this new texture as the [`texture`](https://developer.apple.com/documentation/Metal/MTLRenderPassAttachmentDescriptor/texture) property of an [`MTLRenderPassAttachmentDescriptor`](https://developer.apple.com/documentation/Metal/MTLRenderPassAttachmentDescriptor).

```objective-c
MTLTextureDescriptor *memorylessDescriptor = [MTLTextureDescriptor texture2DDescriptorWithPixelFormat:MTLPixelFormatR16Float
                                                                                                width:256
                                                                                               height:256
                                                                                            mipmapped:YES];
memorylessDescriptor.storageMode = MTLStorageModeMemoryless;
id <MTLTexture> memorylessTexture = [_device newTextureWithDescriptor:memorylessDescriptor];
    
MTLRenderPassDescriptor *renderPassDescriptor = [MTLRenderPassDescriptor renderPassDescriptor];
renderPassDescriptor.depthAttachment.texture = memorylessTexture;
```

See [Rendering a scene with deferred lighting in Objective-C](./rendering-a-scene-with-deferred-lighting-in-objective-c-32e7995538.md) for an example of an app that uses a memoryless render target.

> Note:
> You can create only textures, not buffers, using `doc://com.apple.metal/documentation/Metal/MTLStorageMode/memoryless` mode. You can’t use buffers as memoryless render targets.

---

Copyright © 2026 Apple Inc. All rights reserved. | [Terms of Use](https://www.apple.com/legal/internet-services/terms/site.html) | [Privacy Policy](https://www.apple.com/privacy/privacy-policy)
