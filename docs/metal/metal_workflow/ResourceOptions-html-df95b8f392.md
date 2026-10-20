Source: [https://developer.apple.com/library/archive/documentation/3DDrawing/Conceptual/MTLBestPracticesGuide/ResourceOptions.html](<https://developer.apple.com/library/archive/documentation/3DDrawing/Conceptual/MTLBestPracticesGuide/ResourceOptions.html>)

<a id="//apple_ref/doc/uid/TP40016642-CH17"></a>

<a id="//apple_ref/doc/uid/TP40016642-CH17-SW1"></a>



<a id="resource-options"></a>

## Resource Options

**Best Practice:** Set appropriate resource storage modes and texture usage options.

Your Metal resources must be configured appropriately to take advantage of fast memory access and driver performance optimizations. Resource storage modes allow you to define the storage location and access permissions for your `MTLBuffer` and `MTLTexture` objects. Texture usage options allow you to explicitly declare how you intend to use your `MTLTexture` objects.

<a id="//apple_ref/doc/uid/TP40016642-CH17-DontLinkElementID_19"></a>



<a id="familiarize-yourself-with-device-memory-models"></a>

### Familiarize Yourself with Device Memory Models

Device memory models vary by operating system. iOS and tvOS devices support a *unified* memory model in which the CPU and the GPU share system memory. macOS devices support a *discrete* memory model with CPU-accessible system memory and GPU-accessible video memory.

<a id="//apple_ref/doc/uid/TP40016642-CH17-DontLinkElementID_47"></a>



Important

Some macOS devices feature integrated GPUs. In these devices, the driver optimizes the underlying architecture to support a discrete memory model. macOS Metal apps should always target a discrete memory model.

All iOS and tvOS devices feature integrated GPUs.

<a id="//apple_ref/doc/uid/TP40016642-CH17-DontLinkElementID_20"></a>



<a id="choose-an-appropriate-resource-storage-mode-ios-and-tvos"></a>

### Choose an Appropriate Resource Storage Mode (iOS and tvOS)

In iOS and tvOS, the `Shared` mode defines system memory accessible to both the CPU and the GPU, whereas the `Private` mode defines system memory accessible only to the GPU.

The `Shared` mode is usually the correct choice for iOS and tvOS resources. Choose the `Private` mode only if the CPU never accesses your resource.

<a id="//apple_ref/doc/uid/TP40016642-CH17-DontLinkElementID_48"></a>



Note

In iOS and tvOS, the `memoryless` storage mode is provided for memoryless textures. This storage mode can only be used for temporary render targets stored in on-chip tile memory. For further information, see `Memoryless Textures` in the *[Metal Programming Guide](https://developer.apple.com/library/archive/documentation/Miscellaneous/Conceptual/MetalProgrammingGuide/Introduction/Introduction.html#//apple_ref/doc/uid/TP40014221)*.

<a id="//apple_ref/doc/uid/TP40016642-CH17-SW3"></a>

**Figure 3-1**Resource storage modes in iOS and tvOS
![image: ../Art/ResourceManagement_iOStvOSMemory.pdf](<ResourceOptionshtml/5efbf87ba16ef3f1fc543b4a.png>)

<a id="//apple_ref/doc/uid/TP40016642-CH17-DontLinkElementID_21"></a>



<a id="choose-an-appropriate-resource-storage-mode-macos"></a>

### Choose an Appropriate Resource Storage Mode (macOS)

In macOS, the `Shared` mode defines system memory accessible to both the CPU and the GPU, whereas the `Private` mode defines video memory accessible only to the GPU.

Additionally, macOS implements the `Managed` mode that defines a synchronized memory pair for a resource, with one copy in system memory and another in video memory. Managed resources benefit from fast CPU and GPU access to each copy of the resource, with minimal API calls needed to synchronize these copies.

<a id="//apple_ref/doc/uid/TP40016642-CH17-SW2"></a>

**Figure 3-2**Resource storage modes in macOS
![image: ../Art/ResourceManagement_OSXMemory_2x.png](<ResourceOptionshtml/50f05e0ea0611e7f95a546ec.png>)

<a id="//apple_ref/doc/uid/TP40016642-CH17-DontLinkElementID_49"></a>



Important

In macOS, the `Shared` mode is available only for buffers, not textures. Buffer data is usually linear, resulting in simple GPU access patterns. Textures are more complex and their data is usually tiled or swizzled, resulting in more complicated GPU access patterns.

**Buffer Storage Mode (macOS)**

Use the following guidelines to determine the appropriate storage mode for a particular buffer.

- If the buffer is accessed by the GPU exclusively, choose the `Private` mode. This is a common case for GPU-generated data, such as per-patch tessellation factors.
- If the buffer is accessed by the CPU exclusively, choose the `Shared` mode. This is a rare case and is usually an intermediary step in a blit operation.
- If the buffer is accessed by both the CPU and the GPU, as is the case with most vertex data, consider the following points and refer to [Table 3-1](#//apple_ref/doc/uid/TP40016642-CH17-SW4):

  - For small-sized data that changes frequently, choose the `Shared` mode. The overhead of copying data to video memory may be more expensive than the overhead of the GPU accessing system memory directly.
  - For medium-sized data that changes infrequently, choose the `Managed` mode. Always call an appropriate synchronization method after modifying the contents of a managed buffer.

    After performing a CPU write, call the `didModifyRange:` method to notify Metal about the specific range of data that was modified; this allows Metal to update only that specific range in the video memory copy.

    After encoding a GPU write, encode a blit operation that includes a call to the `synchronizeResource:` method; this allows Metal to update the system memory copy after the associated command buffer has completed execution.
  - For large-sized data that never changes, choose the `Private` mode. Initialize and populate a source buffer with a `Shared` mode and then blit its data into a destination buffer with a `Private` mode. This is an optimal operation with a one-time cost.

<a id="//apple_ref/doc/uid/TP40016642-CH17-SW4"></a>

**Table 3-1**Choosing a storage mode for buffer data accessed by both the CPU and the GPU

| Data size | Resource dirtiness | Update frequency | Storage mode |
| --- | --- | --- | --- |
| Small | Full | Every frame | `Shared` |
| Medium | Partial | Every *n* frames | `Managed` |
| Large | N/A | Once | `Private`  (After a blit from a shared source buffer) |

**Texture Storage Mode (macOS)**

In macOS, the default storage mode for textures is `Managed`. Use the following guidelines to determine the appropriate storage mode for a particular texture.

- If the texture is accessed by the GPU exclusively, choose the `Private` mode. This is a common case for GPU-generated data, such as displayable render targets.
- If the texture is accessed by the CPU exclusively, choose the `Managed` mode. This is a rare case and is usually an intermediary step in a blit operation.
- If the texture is initialized once by the CPU and accessed frequently by the GPU, initialize a source texture with a `Managed` mode and then blit its data into a destination texture with a `Private` mode. This is a common case for static textures, such as diffuse maps.
- If the texture is accessed frequently by both the CPU and GPU, choose the `Managed` mode. This is a common case for dynamic textures, such as image filters. Always call an appropriate synchronization method after modifying the contents of a managed texture.

  To perform a CPU write to a specific region of data and simultaneously notify Metal about the change, call either of the following methods. This allows Metal to update only that specific region in the video memory copy.

  - `replaceRegion:mipmapLevel:withBytes:bytesPerRow:`
  - `replaceRegion:mipmapLevel:slice:withBytes:bytesPerRow:bytesPerImage:`

  After encoding a GPU write, encode a blit operation that includes a call to either of the following methods. This allows Metal to update the system memory copy after the associated command buffer has completed execution.

  - `synchronizeResource:`
  - `synchronizeTexture:slice:level:`

<a id="//apple_ref/doc/uid/TP40016642-CH17-DontLinkElementID_22"></a>



<a id="set-appropriate-texture-usage-flags"></a>

### Set Appropriate Texture Usage Flags

Metal can optimize GPU operations for a given texture, based on its intended use. Always declare explicit texture usage options if you know them in advance. Do not rely on the `Unknown` option; although this option provides the most flexibility for your textures, it incurs a significant performance cost. The driver cannot perform any optimizations if it does not know how you intend to use your texture. For a description of available texture usage options, see the `MTLTextureUsage` reference.

<a id="next_previous"></a>

[Persistent Objects](./PersistentObjects-html-0a8a38ccca.md#//apple_ref/doc/uid/TP40016642-CH4-SW1)

[Triple Buffering](./TripleBuffering-html-4fbf2e3432.md#//apple_ref/doc/uid/TP40016642-CH5-SW1)

Copyright © 2018 Apple Inc. All rights reserved.
[Terms of Use](http://www.apple.com/legal/terms/site.html) |
[Privacy Policy](http://www.apple.com/privacy/) |
[Updated: 2017-03-27](https://developer.apple.com/library/archive/documentation/3DDrawing/Conceptual/MTLBestPracticesGuide/RevisionHistory.html#//apple_ref/doc/uid/TP40016642-CH99-DontLinkElementID_50)
