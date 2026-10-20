Source: [https://developer.apple.com/library/archive/documentation/Miscellaneous/Conceptual/MetalProgrammingGuide/Mem-Obj/Mem-Obj.html](<https://developer.apple.com/library/archive/documentation/Miscellaneous/Conceptual/MetalProgrammingGuide/Mem-Obj/Mem-Obj.html>)

[](https://developer.apple.com/library/archive/documentation/Miscellaneous/Conceptual/MetalProgrammingGuide/Mem-Obj/Mem-Obj.html)[](https://developer.apple.com/library/archive/documentation/Miscellaneous/Conceptual/MetalProgrammingGuide/Mem-Obj/Mem-Obj.html "Resource Objects: Buffers and Textures")
This chapter describes Metal resource objects (`MTLResource`) for storing unformatted memory and formatted image data. There are two types of `MTLResource` objects:

*   `MTLBuffer` represents an allocation of unformatted memory that can contain any type of data. Buffers are often used for vertex, shader, and compute state data.

*   `MTLTexture` represents an allocation of formatted image data with a specified texture type and pixel format. Texture objects are used as source textures for vertex, fragment, or compute functions, as well as to store graphics rendering output (that is, as an attachment).

`MTLSamplerState` objects are also discussed in this chapter. Although samplers are not resources themselves, they are used when performing lookup calculations with a texture object.

[](https://developer.apple.com/library/archive/documentation/Miscellaneous/Conceptual/MetalProgrammingGuide/Mem-Obj/Mem-Obj.html "Buffers Are Typeless Allocations of Memory")
## Buffers Are Typeless Allocations of Memory

A `MTLBuffer` object represents an allocation of memory that can contain any type of data.

[](https://developer.apple.com/library/archive/documentation/Miscellaneous/Conceptual/MetalProgrammingGuide/Mem-Obj/Mem-Obj.html "Creating a Buffer Object")
### Creating a Buffer Object

The following `MTLDevice` methods create and return a `MTLBuffer` object:

*   The `newBufferWithLength:options:` method creates a `MTLBuffer` object with a new storage allocation.

*   The `newBufferWithBytes:length:options:` method creates a `MTLBuffer` object by copying data from existing storage (located at the CPU address `pointer`) into a new storage allocation.

*   The `newBufferWithBytesNoCopy:length:options:deallocator:` method creates a `MTLBuffer` object with an existing storage allocation and does not allocate any new storage for this object.

All buffer creation methods have the input value `length` to indicate the size of the storage allocation, in bytes. All the methods also accept a `MTLResourceOptions` object for `options` that can modify the behavior of the created buffer. If the value for `options` is 0, the default values are used for resource options.

[](https://developer.apple.com/library/archive/documentation/Miscellaneous/Conceptual/MetalProgrammingGuide/Mem-Obj/Mem-Obj.html "Buffer Methods")
### Buffer Methods

The `MTLBuffer` protocol has the following methods:

*   The `contents` method returns the CPU address of the buffer’s storage allocation.

*   The `newTextureWithDescriptor:offset:bytesPerRow:` method creates a special kind of texture object that references the buffer's data. This method is detailed in [Creating a Texture Object](./Mem-Obj-html-7804f9a7f0.md#//apple_ref/doc/uid/TP40014221-CH4-SW10).

[](https://developer.apple.com/library/archive/documentation/Miscellaneous/Conceptual/MetalProgrammingGuide/Mem-Obj/Mem-Obj.html "Textures Are Formatted Image Data")
## Textures Are Formatted Image Data

A `MTLTexture` object represents an allocation of formatted image data that can be used as a resource for a vertex shader, fragment shader, or compute function, or as an attachment to be used as a rendering destination. A `MTLTexture` object can have _one_ of the following structures:

*   A 1D, 2D, or 3D image

*   An array of 1D or 2D images

*   A _cube_ of six 2D images

`MTLPixelFormat` specifies the organization of individual pixels in a `MTLTexture` object. Pixel formats are discussed further in [Pixel Formats for Textures](./Mem-Obj-html-7804f9a7f0.md#//apple_ref/doc/uid/TP40014221-CH4-SW12).

[](https://developer.apple.com/library/archive/documentation/Miscellaneous/Conceptual/MetalProgrammingGuide/Mem-Obj/Mem-Obj.html "Creating a Texture Object")
### Creating a Texture Object

The following methods create and return a `MTLTexture` object:

*   The `newTextureWithDescriptor:` method of `MTLDevice` creates a `MTLTexture` object with a new storage allocation for the texture image data, using a `MTLTextureDescriptor` object to describe the texture’s properties.

*   The `newTextureViewWithPixelFormat:` method of `MTLTexture` creates a `MTLTexture` object that shares the same storage allocation as the calling `MTLTexture` object. Since they share the same storage, any changes to the pixels of the new texture object are reflected in the calling texture object, and vice versa. For the newly created texture, the `newTextureViewWithPixelFormat:` method reinterprets the existing texture image data of the storage allocation of the calling `MTLTexture` object as if the data was stored in the specified pixel format. The `MTLPixelFormat` of the new texture object must be _compatible_ with the `MTLPixelFormat` of the original texture object. (See [Pixel Formats for Textures](./Mem-Obj-html-7804f9a7f0.md#//apple_ref/doc/uid/TP40014221-CH4-SW12) for details about the ordinary, packed, and compressed pixel formats.)

*   The `newTextureWithDescriptor:offset:bytesPerRow:` method of `MTLBuffer` creates a `MTLTexture` object that shares the storage allocation of the calling `MTLBuffer` object as its texture image data. As they share the same storage, any changes to the pixels of the new texture object are reflected in the calling texture object, and vice versa. Sharing storage between a texture and a buffer can prevent the use of certain texturing optimizations, such as pixel swizzling or tiling.

[](https://developer.apple.com/library/archive/documentation/Miscellaneous/Conceptual/MetalProgrammingGuide/Mem-Obj/Mem-Obj.html "Creating a Texture Object with a Texture Descriptor")
#### Creating a Texture Object with a Texture Descriptor

`MTLTextureDescriptor` defines the properties that are used to create a `MTLTexture` object, including its image size (width, height, and depth), pixel format, arrangement (array or cube type) and number of mipmaps. The `MTLTextureDescriptor` properties are only used during the creation of a `MTLTexture` object. After you create a `MTLTexture` object, property changes in its `MTLTextureDescriptor` object no longer have any effect on that texture.

To create one or more textures from a descriptor:

1.   Create a custom `MTLTextureDescriptor` object that contains texture properties that describe the texture data:

    *   The `textureType` property specifies a texture’s dimensionality and arrangement (for example, array or cube).

    *   The `width`, `height`, and `depth` properties specify the pixel size in each dimension of the base level texture mipmap.

    *   The `pixelFormat` property specifies how a pixel is stored in a texture.

    *   The `arrayLength` property specifies the number of array elements for a `MTLTextureType1DArray` or `MTLTextureType2DArray` type texture object.

    *   The `mipmapLevelCount` property specifies the number of mipmap levels.

    *   The `sampleCount` property specifies the number of samples in each pixel.

    *   The `resourceOptions` property specifies the behavior of its memory allocation.

2.   Create a texture from the `MTLTextureDescriptor` object by calling the `newTextureWithDescriptor:` method of a `MTLDevice` object. After texture creation, call the `replaceRegion:mipmapLevel:slice:withBytes:bytesPerRow:bytesPerImage:` method to load the texture image data, as detailed in [Copying Image Data to and from a Texture](./Mem-Obj-html-7804f9a7f0.md#//apple_ref/doc/uid/TP40014221-CH4-SW17).

3.   To create more `MTLTexture` objects, you can reuse the same `MTLTextureDescriptor` object, modifying the descriptor’s property values as needed.

Listing 3-1 shows code for creating a texture descriptor `txDesc` and setting its properties for a 3D, 64x64x64 texture.

[](https://developer.apple.com/library/archive/documentation/Miscellaneous/Conceptual/MetalProgrammingGuide/Mem-Obj/Mem-Obj.html "Listing 3-1Creating a Texture Object with a Custom Texture Descriptor")
**Listing 3-1**Creating a Texture Object with a Custom Texture Descriptor

MTLTextureDescriptor* txDesc = [[MTLTextureDescriptor alloc] init];
txDesc.textureType = MTLTextureType3D;
txDesc.height = 64;
txDesc.width = 64;
txDesc.depth = 64;
txDesc.pixelFormat = MTLPixelFormatBGRA8Unorm;
txDesc.arrayLength = 1;
txDesc.mipmapLevelCount = 1;
id <MTLTexture> aTexture = [device newTextureWithDescriptor:txDesc];

[](https://developer.apple.com/library/archive/documentation/Miscellaneous/Conceptual/MetalProgrammingGuide/Mem-Obj/Mem-Obj.html "Working with Texture Slices")
#### Working with Texture Slices

A _slice_ is a single 1D, 2D, or 3D texture image and all its associated mipmaps. For each slice:

*   The size of the base level mipmap is specified by the `width`, `height`, and `depth` properties of the `MTLTextureDescriptor` object.

*   The scaled size of mipmap level _i_ is specified by max(1, floor(`width` / 2 i)) x max(1, floor(`height` / 2 i)) x max(1, floor(`depth` / 2 i)). The maximum mipmap level is the first mipmap level where the size 1 x 1 x 1 is achieved.

*   The number of mipmap levels in one slice can be determined by floor(log 2(max(`width`, `height`, `depth`)))+1.

All texture objects have at least one slice; cube and array texture types may have several slices. In the methods that write and read texture image data that are discussed in [Copying Image Data to and from a Texture](./Mem-Obj-html-7804f9a7f0.md#//apple_ref/doc/uid/TP40014221-CH4-SW17), `slice` is a zero-based input value. For a 1D, 2D, or 3D texture, there is only one slice, so the value of `slice` must be 0. A cube texture has six total 2D slices, addressed from 0 to 5. For the 1DArray and 2DArray texture types, each array element represents one slice. For example, for a 2DArray texture type with `arrayLength` = 10, there are 10 total slices, addressed from 0 to 9. To choose a single 1D, 2D, or 3D image out of an overall texture structure, first select a slice, and then select a mipmap level within that slice.

[](https://developer.apple.com/library/archive/documentation/Miscellaneous/Conceptual/MetalProgrammingGuide/Mem-Obj/Mem-Obj.html "Creating a Texture Descriptor with Convenience Methods")
#### Creating a Texture Descriptor with Convenience Methods

For common 2D and cube textures, use the following convenience methods to create a `MTLTextureDescriptor` object with several of its property values automatically set:

*   The `texture2DDescriptorWithPixelFormat:width:height:mipmapped:` method creates a `MTLTextureDescriptor` object for a 2D texture. The `width` and `height` values define the dimensions of the 2D texture. The `type` property is automatically set to `MTLTextureType2D`, and `depth` and `arrayLength` are set to 1.

*   The `textureCubeDescriptorWithPixelFormat:size:mipmapped:` method creates a `MTLTextureDescriptor` object for a cube texture, where the `type` property is set to `MTLTextureTypeCube`, `width` and `height` are set to size, and `depth` and `arrayLength` are set to 1.

Both `MTLTextureDescriptor` convenience methods accept an input value, `pixelFormat`, which defines the pixel format of the texture. Both methods also accept the input value `mipmapped`, which determines whether or not the texture image is mipmapped. (If `mipmapped` is `YES`, the texture is mipmapped.)

Listing 3-2 uses the `texture2DDescriptorWithPixelFormat:width:height:mipmapped:` method to create a descriptor object for a `64x64` 2D texture that is not mipmapped.

[](https://developer.apple.com/library/archive/documentation/Miscellaneous/Conceptual/MetalProgrammingGuide/Mem-Obj/Mem-Obj.html "Listing 3-2Creating a Texture Object with a Convenience Texture Descriptor")
**Listing 3-2**Creating a Texture Object with a Convenience Texture Descriptor

MTLTextureDescriptor *texDesc = [MTLTextureDescriptor 
         texture2DDescriptorWithPixelFormat:MTLPixelFormatBGRA8Unorm 
         width:64 height:64 mipmapped:NO];
id <MTLTexture> myTexture = [device newTextureWithDescriptor:texDesc];

[](https://developer.apple.com/library/archive/documentation/Miscellaneous/Conceptual/MetalProgrammingGuide/Mem-Obj/Mem-Obj.html "Copying Image Data to and from a Texture")
#### Copying Image Data to and from a Texture

To synchronously copy image data into or copy data from the storage allocation of a `MTLTexture` object, use the following methods:

*   `replaceRegion:mipmapLevel:slice:withBytes:bytesPerRow:bytesPerImage:` copies a region of pixel data from the caller's pointer into a portion of the storage allocation of a specified texture slice. `replaceRegion:mipmapLevel:withBytes:bytesPerRow:` is a similar convenience method that copies a region of pixel data into the default slice, assuming default values for slice-related arguments (i.e., `slice` = 0 and `bytesPerImage` = 0).

*   `getBytes:bytesPerRow:bytesPerImage:fromRegion:mipmapLevel:slice:` retrieves a region of pixel data from a specified texture slice. `getBytes:bytesPerRow:fromRegion:mipmapLevel:` is a similar convenience method that retrieves a region of pixel data from the default slice, assuming default values for slice-related arguments (`slice` = 0 and `bytesPerImage` = 0).

Listing 3-3 shows how to call `replaceRegion:mipmapLevel:slice:withBytes:bytesPerRow:bytesPerImage:` to specify a texture image from source data in system memory, `textureData`, at slice `0` and mipmap level `0`.

[](https://developer.apple.com/library/archive/documentation/Miscellaneous/Conceptual/MetalProgrammingGuide/Mem-Obj/Mem-Obj.html "Listing 3-3Copying Image Data into the Texture")
**Listing 3-3**Copying Image Data into the Texture

//  pixelSize is the size of one pixel, in bytes
//  width, height - number of pixels in each dimension
NSUInteger myRowBytes = width * pixelSize;
NSUInteger myImageBytes = rowBytes * height;
[tex replaceRegion:MTLRegionMake2D(0,0,width,height)
mipmapLevel:0 slice:0 withBytes:textureData
bytesPerRow:myRowBytes bytesPerImage:myImageBytes];

[](https://developer.apple.com/library/archive/documentation/Miscellaneous/Conceptual/MetalProgrammingGuide/Mem-Obj/Mem-Obj.html "Pixel Formats for Textures")
### Pixel Formats for Textures

`MTLPixelFormat` specifies the organization of color, depth, and stencil data storage in individual pixels of a `MTLTexture` object. There are three varieties of pixel formats: ordinary, packed, and compressed.

*   Ordinary formats have only regular 8-, 16-, or 32-bit color components. Each component is arranged in increasing memory addresses with the first listed component at the lowest address. For example, `MTLPixelFormatRGBA8Unorm` is a 32-bit format with eight bits for each color component; the lowest addresses contains red, the next addresses contain green, and so on. In contrast, for `MTLPixelFormatBGRA8Unorm`, the lowest addresses contains blue, the next addresses contain green, and so on.

*   Packed formats combine multiple components into one 16-bit or 32-bit value, where the components are stored from the least to most significant bit (LSB to MSB). For example, `MTLPixelFormatRGB10A2Uint` is a 32-bit packed format that consists of three 10-bit channels (for R, G, and B) and two bits for alpha.

*   Compressed formats are arranged in blocks of pixels, and the layout of each block is specific to that pixel format. Compressed pixel formats can only be used for 2D, 2D Array, or cube texture types. Compressed formats cannot be used to create 1D, 2DMultisample or 3D textures.

The `MTLPixelFormatGBGR422` and `MTLPixelFormatBGRG422` are special pixel formats that are intended to store pixels in the YUV color space. These formats are only supported for 2D textures (but neither 2D Array, nor cube type), without mipmaps, and an even `width`.

Several pixel formats store color components with sRGB color space values (for example, `MTLPixelFormatRGBA8Unorm_sRGB` or `MTLPixelFormatETC2_RGB8_sRGB`). When a sampling operation references a texture with an sRGB pixel format, the Metal implementation converts the sRGB color space components to a linear color space before the sampling operation takes place. The conversion from an sRGB component, S, to a linear component, L, is as follows:

*   If S <= 0.04045, L = S/12.92

*   If S > 0.04045, L = ((S+0.055)/1.055)2.4

Conversely, when rendering to a color-renderable attachment that uses a texture with an sRGB pixel format, the implementation converts the linear color values to sRGB, as follows:

*   If L <= 0.0031308, S = L * 12.92

*   If L > 0.0031308, S = (1.055 * L 0.41667) - 0.055

For more information about pixel format for rendering, see [Creating a Render Pass Descriptor](./Render-Ctx-html-760b5413cd.md#//apple_ref/doc/uid/TP40014221-CH7-SW5).

[](https://developer.apple.com/library/archive/documentation/Miscellaneous/Conceptual/MetalProgrammingGuide/Mem-Obj/Mem-Obj.html "Creating a Sampler States Object for Texture Lookup")
## Creating a Sampler States Object for Texture Lookup

A `MTLSamplerState` object defines the addressing, filtering, and other properties that are used when a graphics or compute function performs texture sampling operations on a `MTLTexture` object. A sampler descriptor defines the properties of a sampler state object. To create a sampler state object:

1.   Call the `newSamplerStateWithDescriptor:` method of a `MTLDevice` object to create a `MTLSamplerDescriptor` object.

2.   Set the desired values in the `MTLSamplerDescriptor` object, including filtering options, addressing modes, maximum anisotropy, and level-of-detail parameters.

3.   Create a `MTLSamplerState` object from the sampler descriptor by calling the `newSamplerStateWithDescriptor:` method of the `MTLDevice` object that created the descriptor.

You can reuse the sampler descriptor object to create more `MTLSamplerState` objects, modifying the descriptor’s property values as needed. The descriptor's properties are only used during object creation. After a sampler state has been created, changing the properties in its descriptor no longer has an effect on that sampler state.

Listing 3-4 is a code example that creates a `MTLSamplerDescriptor` and configures it in order to create a `MTLSamplerState`. Non-default values are set for filter and address mode properties of the descriptor object. Then the `newSamplerStateWithDescriptor:` method uses the sampler descriptor to create a sampler state object.

[](https://developer.apple.com/library/archive/documentation/Miscellaneous/Conceptual/MetalProgrammingGuide/Mem-Obj/Mem-Obj.html "Listing 3-4Creating a Sampler State Object")
**Listing 3-4**Creating a Sampler State Object

// create MTLSamplerDescriptor
MTLSamplerDescriptor *desc = [[MTLSamplerDescriptor alloc] init];
desc.minFilter = MTLSamplerMinMagFilterLinear;
desc.magFilter = MTLSamplerMinMagFilterLinear;
desc.sAddressMode = MTLSamplerAddressModeRepeat;
desc.tAddressMode = MTLSamplerAddressModeRepeat;
//  all properties below have default values
desc.mipFilter        = MTLSamplerMipFilterNotMipmapped;
desc.maxAnisotropy    = 1U;
desc.normalizedCoords = YES;
desc.lodMinClamp      = 0.0f;
desc.lodMaxClamp      = FLT_MAX;
// create MTLSamplerState
id <MTLSamplerState> sampler = [device newSamplerStateWithDescriptor:desc];

[](https://developer.apple.com/library/archive/documentation/Miscellaneous/Conceptual/MetalProgrammingGuide/Mem-Obj/Mem-Obj.html "Maintaining Coherency Between CPU and GPU Memory")
## Maintaining Coherency Between CPU and GPU Memory

Both the CPU and GPU can access the underlying storage for a `MTLResource` object. However, the GPU operates asynchronously from the host CPU, so keep the following in mind when using the host CPU to access the storage for these resources.

When executing a `MTLCommandBuffer` object, the `MTLDevice` object is only guaranteed to observe any changes made by the host CPU to the storage allocation of any `MTLResource` object referenced by that `MTLCommandBuffer` object if (and only if) those changes were made by the host CPU before the `MTLCommandBuffer` object was committed. That is, the `MTLDevice` object might not observe changes to the resource that the host CPU makes after the corresponding `MTLCommandBuffer` object was committed (i.e., the `status` property of the `MTLCommandBuffer` object is `MTLCommandBufferStatusCommitted`).

Similarly, after the `MTLDevice` object executes a `MTLCommandBuffer` object, the host CPU is only guaranteed to observe any changes the `MTLDevice` object makes to the storage allocation of any resource referenced by that command buffer if the command buffer has completed execution (that is, the `status` property of the `MTLCommandBuffer` object is `MTLCommandBufferStatusCompleted`).