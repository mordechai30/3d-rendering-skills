Source: [https://developer.apple.com/documentation/metal/copying-data-to-a-private-resource?language=objc](<https://developer.apple.com/documentation/metal/copying-data-to-a-private-resource?language=objc>)

<a id="copying-data-to-a-private-resource"></a>

# Copying data to a private resource

Use a blit command encoder to copy buffer or texture data to a private resource.

<a id="discussion"></a>

## Discussion

Resources with an [`MTLStorageMode.private`](https://developer.apple.com/documentation/Metal/MTLStorageMode/private) storage mode are accessible only to the GPU. Private resources perform better than shared resources, and you don’t have to explicitly synchronize them the way you do for managed resources.

However, because private resources aren’t accessible to the CPU, you can’t populate them with it. To write data from the CPU to a private resource, you need to first write the data to a shared or managed resource. You can then copy the data from that resource to the private resource.

For more information about resource storage modes, see [Setting resource storage modes](https://developer.apple.com/documentation/Metal/setting-resource-storage-modes).

<a id="copying-data-from-a-shared-buffer-to-a-private-buffer"></a>

### Copying data from a shared buffer to a private buffer

First, create a shared buffer and populate its contents using the [`makeBuffer(bytes:length:options:)`](https://developer.apple.com/documentation/Metal/MTLDevice/makeBuffer(bytes:length:options:)) method.

```objective-c
// Create and populate a source buffer.
id <MTLBuffer> _sourceBuffer;
_sourceBuffer = [_device newBufferWithBytes:bufferData
                                     length:bufferLength
                                    options:MTLResourceStorageModeShared];
```

Next, create a private buffer that’s large enough to store your buffer data using the [`makeBuffer(length:options:)`](https://developer.apple.com/documentation/Metal/MTLDevice/makeBuffer(length:options:)) method.

```objective-c
// Create a private buffer.
id <MTLBuffer> _privateBuffer;
_privateBuffer = [_device newBufferWithLength:bufferLength
                                      options:MTLResourceStorageModePrivate];
```

Finally, encode and commit an [`copy(from:sourceOffset:to:destinationOffset:size:)`](https://developer.apple.com/documentation/Metal/MTLBlitCommandEncoder/copy(from:sourceOffset:to:destinationOffset:size:)) command. Set the shared buffer as the `sourceBuffer` parameter. Set the private buffer as the `destinationBuffer` parameter.

```objective-c
// Create a command buffer for GPU work.
id <MTLCommandBuffer> commandBuffer = [_commandQueue commandBuffer];

// Encode a blit pass to copy data from the source buffer to the private buffer.
id <MTLBlitCommandEncoder> blitCommandEncoder = [commandBuffer blitCommandEncoder];
[blitCommandEncoder copyFromBuffer:_sourceBuffer
                      sourceOffset:0
                          toBuffer:_privateBuffer
                 destinationOffset:0 size:bufferLength];
[blitCommandEncoder endEncoding];

// Add a completion handler and commit the command buffer.
[commandBuffer addCompletedHandler:^(id<MTLCommandBuffer> cb) {
    // Populate private buffer.
}];
[commandBuffer commit];
```

> Note:
> In macOS, Metal doesn’t reformat buffer contents or layout to improve GPU access. There’s no difference in GPU performance between managed or private buffers, so there’s no performance benefit in copying data from a managed buffer to a private buffer.

<a id="copying-data-from-a-shared-buffer-to-a-private-texture"></a>

### Copying data from a shared buffer to a private texture

Use this implementation to copy texture data from the CPU to a private texture in one operation, without having to synchronize a managed texture.

First, create a shared buffer and populate its contents with your texture data.

```objective-c
// Create and populate a source buffer with texture data.
id <MTLBuffer> _sourceBuffer;
_sourceBuffer = [_device newBufferWithBytes:textureData
                                     length:pixelSize*textureSize.width*textureSize.height
                                    options:MTLResourceStorageModeShared];
```

Next, create a private texture with a suitable configuration for the texture data.

```objective-c
// Create a texture descriptor.
MTLTextureDescriptor *textureDescriptor = [MTLTextureDescriptor texture2DDescriptorWithPixelFormat:MTLPixelFormatRGBA8Unorm
                                                                                             width:textureSize.width
                                                                                            height:textureSize.height
                                                                                         mipmapped:NO];

// Set the texture descriptor's storage mode to private.
textureDescriptor.storageMode = MTLStorageModePrivate;

// Create a private texture.
id <MTLTexture> _privateTexture;
_privateTexture = [_device newTextureWithDescriptor:textureDescriptor];
```

Finally, encode and commit an [`copy(from:sourceOffset:sourceBytesPerRow:sourceBytesPerImage:sourceSize:to:destinationSlice:destinationLevel:destinationOrigin:)`](https://developer.apple.com/documentation/Metal/MTLBlitCommandEncoder/copy(from:sourceOffset:sourceBytesPerRow:sourceBytesPerImage:sourceSize:to:destinationSlice:destinationLevel:destinationOrigin:)) command. Set the shared buffer as the `sourceBuffer` parameter. Set the private texture as the `destinationTexture` parameter.

```objective-c
// Create a command buffer for GPU work.
id <MTLCommandBuffer> commandBuffer = [_commandQueue commandBuffer];

// Encode a blit pass to copy data from the source buffer to the private texture.
id <MTLBlitCommandEncoder> blitCommandEncoder = [commandBuffer blitCommandEncoder];
[blitCommandEncoder copyFromBuffer:_sourceBuffer
                      sourceOffset:0
                 sourceBytesPerRow:pixelSize*textureSize.width
               sourceBytesPerImage:pixelSize*textureSize.width*textureSize.height
                        sourceSize:textureSize
                         toTexture:_privateTexture
                  destinationSlice:0
                  destinationLevel:0
                 destinationOrigin:textureOrigin];
[blitCommandEncoder endEncoding];

// Add a completion handler and commit the command buffer.
[commandBuffer addCompletedHandler:^(id<MTLCommandBuffer> cb) {
    // Private texture is populated.
}];
[commandBuffer commit];
```

<a id="copying-data-from-a-shared-or-managed-texture-to-a-private-texture"></a>

### Copying data from a shared or managed texture to a private texture

First, create a shared texture or for Mac apps, a managed texture. For more information about creating buffers and textures with specific storage modes, see [Setting resource storage modes](https://developer.apple.com/documentation/Metal/setting-resource-storage-modes).

Then populate the contents of the source texture using the [`replace(region:mipmapLevel:withBytes:bytesPerRow:)`](https://developer.apple.com/documentation/Metal/MTLTexture/replace(region:mipmapLevel:withBytes:bytesPerRow:)) method.

```objective-c
// Create and populate a source texture.
id <MTLTexture> _sourceTexture;
_sourceTexture = [_device newTextureWithDescriptor:textureDescriptor];
[_sourceTexture replaceRegion:MTLRegionMake2D(textureOrigin.x, textureOrigin.y, textureSize.width, textureSize.height)
                  mipmapLevel:0
                    withBytes:textureData
                  bytesPerRow:pixelSize*textureSize.width];
```

Next, create a private texture with a suitable configuration for your texture data. If appropriate, reuse the texture descriptor that you configured for the shared or managed texture.

```objective-c
// Set the texture descriptor's storage mode to `MTLStorageModePrivate`.
textureDescriptor.storageMode = MTLStorageModePrivate;

// Create a private texture.
id <MTLTexture> _privateTexture;
_privateTexture = [_device newTextureWithDescriptor:textureDescriptor];
```

Finally, encode and commit an [`copy(from:sourceSlice:sourceLevel:sourceOrigin:sourceSize:to:destinationSlice:destinationLevel:destinationOrigin:)`](https://developer.apple.com/documentation/Metal/MTLBlitCommandEncoder/copy(from:sourceSlice:sourceLevel:sourceOrigin:sourceSize:to:destinationSlice:destinationLevel:destinationOrigin:)) command. Set the shared or managed texture as the `sourceTexture` parameter. Set the private texture as the `destinationTexture` parameter.

```objective-c
// Create a command buffer for GPU work.
id <MTLCommandBuffer> commandBuffer = [_commandQueue commandBuffer];

// Encode a blit pass to copy data from the source texture to the private texture.
id <MTLBlitCommandEncoder> blitCommandEncoder = [commandBuffer blitCommandEncoder];
[blitCommandEncoder copyFromTexture:_sourceTexture
                        sourceSlice:0
                        sourceLevel:0
                       sourceOrigin:textureOrigin
                         sourceSize:textureSize
                          toTexture:_privateTexture
                   destinationSlice:0
                   destinationLevel:0
                  destinationOrigin:textureOrigin];
[blitCommandEncoder endEncoding];

// Add a completion handler and commit the command buffer.
[commandBuffer addCompletedHandler:^(id<MTLCommandBuffer> cb) {
    // Private texture is populated.
}];
[commandBuffer commit];
```

Copying data from a managed texture to a private texture involves two copy operations. For the first operation, Metal synchronizes the managed texture and copies the texture data from CPU-accessible memory to GPU-accessible memory. For the second operation, Metal copies the texture data from the managed texture to the private texture.

<a id="copying-data-from-a-private-texture-to-a-shared-buffer"></a>

### Copying data from a private texture to a shared buffer

Use this implementation to copy texture data from the GPU to a shared buffer, without having to synchronize a managed texture.

First, create a private texture.

```objective-c
// Create a texture descriptor.
MTLTextureDescriptor *textureDescriptor = [MTLTextureDescriptor texture2DDescriptorWithPixelFormat:MTLPixelFormatRGBA8Unorm
                                                                                             width:textureSize.width
                                                                                            height:textureSize.height
                                                                                         mipmapped:NO];

// Set the texture descriptor's storage mode to `MTLStorageModePrivate`.
textureDescriptor.storageMode = MTLStorageModePrivate;

// Create a private texture.
id <MTLTexture> _sourceTexture;
_sourceTexture = [_device newTextureWithDescriptor:textureDescriptor];
```

Next, create a shared buffer that’s large enough to store your texture data.

```objective-c
// Create a shared buffer.
id <MTLBuffer> _sharedBuffer;
_sharedBuffer = [_device newBufferWithLength: pixelSize*textureSize.width*textureSize.height
                                     options: MTLResourceStorageModeShared];
```

Next, encode a compute, render, or blit pass to populate the contents of your private texture.

```objective-c
// Create a command buffer for GPU work.
id <MTLCommandBuffer> commandBuffer = [_commandQueue commandBuffer];

/* Encode a compute, render, or blit pass to populate the source texture's contents. */
/* ... */
```

Finally, encode and commit an [`copy(from:sourceSlice:sourceLevel:sourceOrigin:sourceSize:to:destinationOffset:destinationBytesPerRow:destinationBytesPerImage:)`](https://developer.apple.com/documentation/Metal/MTLBlitCommandEncoder/copy(from:sourceSlice:sourceLevel:sourceOrigin:sourceSize:to:destinationOffset:destinationBytesPerRow:destinationBytesPerImage:)) command. Set the private texture as the `sourceTexture` parameter. Set the shared buffer as the `destinationBuffer` parameter.

```objective-c
// Encode a blit pass to copy data from the source texture to the shared buffer.
id <MTLBlitCommandEncoder> blitCommandEncoder = [commandBuffer blitCommandEncoder];
[blitCommandEncoder copyFromTexture:_sourceTexture
                        sourceSlice:0
                        sourceLevel:0
                       sourceOrigin:textureOrigin
                         sourceSize:textureSize
                           toBuffer:_sharedBuffer
                  destinationOffset:0
             destinationBytesPerRow:pixelSize*textureSize.width
           destinationBytesPerImage:pixelSize*textureSize.width*textureSize.height];
[blitCommandEncoder endEncoding];

// Add a completion handler and commit the command buffer.
[commandBuffer addCompletedHandler:^(id<MTLCommandBuffer> cb) {
    // Shared buffer is populated.
}];
[commandBuffer commit];
```

---

Copyright © 2026 Apple Inc. All rights reserved. | [Terms of Use](https://www.apple.com/legal/internet-services/terms/site.html) | [Privacy Policy](https://www.apple.com/privacy/privacy-policy)
