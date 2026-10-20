Source: [https://developer.apple.com/documentation/metal/improving-cpu-performance-by-using-argument-buffers?language=objc](<https://developer.apple.com/documentation/metal/improving-cpu-performance-by-using-argument-buffers?language=objc>)

<a id="improving-cpu-performance-by-using-argument-buffers"></a>

# Improving CPU performance by using argument buffers

Optimize your app’s performance by grouping your resources into argument buffers.

<a id="discussion"></a>

## Discussion

Use argument buffers to gather multiple resources into a single shader argument. An *argument buffer* is a Metal buffer that contains references to other Metal resources, including [`MTLBuffer`](https://developer.apple.com/documentation/Metal/MTLBuffer), [`MTLTexture`](https://developer.apple.com/documentation/Metal/MTLTexture), [`MTLSamplerState`](https://developer.apple.com/documentation/Metal/MTLSamplerState), and [`MTLAccelerationStructure`](https://developer.apple.com/documentation/Metal/MTLAccelerationStructure) instances. Argument buffers use less overhead than assigning each resource individually. This is especially true for resources that don’t change between frames because you can assign the argument buffer once and reuse it many times.

> Note:
> You need to use argument buffers to bind resources to pipelines composed of shaders that you compile with the [Metal shader converter](https://developer.apple.com/metal/shader-converter/).

For more information on argument buffers, watch [Go bindless with Metal 3](https://developer.apple.com/videos/play/wwdc2022/10101/) and [Explore bindless rendering in Metal](https://developer.apple.com/wwdc21/10286).

<a id="define-argument-buffer-formats-in-metal-shading-language"></a>

### Define argument buffer formats in Metal shading language

Declare your argument buffers in a Metal Shading Language (MSL) source file as structures.

```metal
struct ArgumentBufferExample{
    texture2d<float, access::write> a;
    depth2d<float> b;
    sampler c;
    texture2d<float> d;
    device float4* e;
    texture2d<float> f;
    int g;
};

kernel void example(constant ArgumentBufferExample & argumentBuffer [[buffer(0)]])
{
    // 
    ...
}
```

Add the following types to the structures:

- Basic scalar data types, such as `half` and `float`
- Basic vector and matrix data types, such as `half4` and `float4x4`
- Textures, such as `texture2d`
- Samplers, such as a linear sampler
- Acceleration structures
- Indirect command buffers
- Arrays and structures that store the types above
- Other arrays and structures

> Note:
> Argument buffers can’t contain union types, although instances that adopt the `doc://com.apple.metal/documentation/Metal/MTLBuffer` protocol support unions.

<a id="encode-resources-into-argument-buffers"></a>

### Encode resources into argument buffers

Structures in regular Metal buffers define the exact layout of the data in memory. The memory layout for argument buffers depends on the GPU’s support for argument buffers and the device’s OS version. Metal divides argument buffer support into two tiers: Tier 1 and Tier 2. For Tier 2, argument buffers match the memory layout of an equivalent C structure on these OS releases:

- iOS 16.0 and later
- tvOS 16.0 and later
- macOS 13.0 and later

To directly encode the argument buffer resources on these Tier 2 devices, write the [`MTLBuffer`](https://developer.apple.com/documentation/Metal/MTLBuffer)`.`[`gpuAddress`](https://developer.apple.com/documentation/Metal/MTLBuffer/gpuAddress) property — and for other resource types (samplers, textures, and acceleration structures), the [`gpuResourceID`](https://developer.apple.com/documentation/Metal/MTLComputePipelineState/gpuResourceID) property — into the corresponding structure member. To encode offsets, treat these property values as `uint64` types and add the offset to them.

For Tier 1 devices and older OS versions on Tier 2 devices, buffers have a private memory layout that can vary by GPU. For these devices, use an [`MTLArgumentEncoder`](https://developer.apple.com/documentation/Metal/MTLArgumentEncoder) instance to encode an argument buffer’s data into a destination [`MTLBuffer`](https://developer.apple.com/documentation/Metal/MTLBuffer) instance. Then pass the argument buffer as a parameter to an [`MTLRenderCommandEncoder`](https://developer.apple.com/documentation/Metal/MTLRenderCommandEncoder) or [`MTLComputeCommandEncoder`](https://developer.apple.com/documentation/Metal/MTLComputeCommandEncoder) graphics or compute function, such as the following:

- [`setVertexBuffer(_:offset:index:)`](https://developer.apple.com/documentation/Metal/MTLRenderCommandEncoder/setVertexBuffer(_:offset:index:))
- [`setFragmentBuffer(_:offset:index:)`](https://developer.apple.com/documentation/Metal/MTLRenderCommandEncoder/setFragmentBuffer(_:offset:index:))
- [`setMeshBuffer(_:offset:index:)`](https://developer.apple.com/documentation/Metal/MTLRenderCommandEncoder/setMeshBuffer(_:offset:index:))
- [`setObjectBuffer(_:offset:index:)`](https://developer.apple.com/documentation/Metal/MTLRenderCommandEncoder/setObjectBuffer(_:offset:index:))
- [`setTileBuffer(_:offset:index:)`](https://developer.apple.com/documentation/Metal/MTLRenderCommandEncoder/setTileBuffer(_:offset:index:))
- [`setBuffer(_:offset:index:)`](https://developer.apple.com/documentation/Metal/MTLComputeCommandEncoder/setBuffer(_:offset:index:))

You can encode resources into argument buffers using the following types:

- [`MTLBuffer`](https://developer.apple.com/documentation/Metal/MTLBuffer)
- [`MTLTexture`](https://developer.apple.com/documentation/Metal/MTLTexture)
- [`MTLSamplerState`](https://developer.apple.com/documentation/Metal/MTLSamplerState)
- <doc://com.apple.documentation/documentation/simd/simd_float1>, <doc://com.apple.documentation/documentation/simd/simd_float4>, and other inlined constant data
- [`MTLAccelerationStructure`](https://developer.apple.com/documentation/Metal/MTLAccelerationStructure)
- [`MTLIndirectCommandBuffer`](https://developer.apple.com/documentation/Metal/MTLIndirectCommandBuffer)
- [`MTLComputePipelineState`](https://developer.apple.com/documentation/Metal/MTLComputePipelineState)
- [`MTLRenderPipelineState`](https://developer.apple.com/documentation/Metal/MTLRenderPipelineState)

<a id="use-heaps-to-improve-efficiency"></a>

### Use heaps to improve efficiency

Encoding resources into argument buffers eliminates the need for the Metal driver to capture state and track residency when it assigns individual resources to the indices of a function’s argument table. Argument buffers provide greater control over resource residency, which you need to explicitly declare before issuing draw or dispatch calls.

When you combine resource heaps with argument buffers, you can further reduce overhead by making all read-only resources backed by an [`MTLHeap`](https://developer.apple.com/documentation/Metal/MTLHeap) with a single call to the `useHeap` method. However, you still need to call the `useResource` method for each writable resource, even when your pass only intends to read from it.

Finally, argument buffers allow Metal to index resources dynamically at function execution time, which increases the limit on the number of resources that it can place inside the buffers.

<a id="understand-argument-buffer-tier-limits-and-capabilities"></a>

### Understand argument buffer tier limits and capabilities

Use the [`argumentBuffersSupport`](https://developer.apple.com/documentation/Metal/MTLDevice/argumentBuffersSupport) property of the [`MTLDevice`](https://developer.apple.com/documentation/Metal/MTLDevice) instance to get its tier.

**Common Tier 1 and Tier 2 Limits**

On iOS and tvOS, the maximum number of unique samplers per app is `96`, and for macOS, `1024` or greater, depending on the device and OS version.These limits are only applicable to samplers that have their [`supportArgumentBuffers`](https://developer.apple.com/documentation/Metal/MTLSamplerDescriptor/supportArgumentBuffers) property set to <doc://com.apple.documentation/documentation/Swift/true>. Use the [`MTLDevice`](https://developer.apple.com/documentation/Metal/MTLDevice)`.`[`maxArgumentBufferSamplerCount`](https://developer.apple.com/documentation/Metal/MTLDevice/maxArgumentBufferSamplerCount) property to get the exact maximum number of unique samplers per app for a device.

Metal considers an [`MTLSamplerState`](https://developer.apple.com/documentation/Metal/MTLSamplerState) instance unique if the configuration of its originating [`MTLSamplerDescriptor`](https://developer.apple.com/documentation/Metal/MTLSamplerDescriptor) properties is unique. For example, if two samplers have equal [`minFilter`](https://developer.apple.com/documentation/Metal/MTLSamplerDescriptor/minFilter) values but different [`magFilter`](https://developer.apple.com/documentation/Metal/MTLSamplerDescriptor/magFilter) values, Metal considers them different instances.

For the maximum number of entries in each function argument table, see [Metal feature set tables](improving-cpu-performance-by-using-argument-buffers/9f31df15dd6827545702c5a0.pdf).

**Tier 1 Limits**

For Tier 1, Metal imposes resource limits on the maximum combined number of resources set within an argument buffer and set individually, per graphics or compute function. Metal counts the argument buffer entries against the maximum buffer entries in each function argument table. For example, if a kernel function uses four individual textures and one argument buffer with eight textures, the total number of textures for that kernel function is 12. Tier 1 argument buffers can’t include writable textures.

Other Tier 1 limits on argument buffers are:

- Need to be immutable because the GPU can’t modify the contents of an argument buffer
- Need to be CPU-accessible, so set the buffer’s storage mode to either [`MTLStorageMode.shared`](https://developer.apple.com/documentation/Metal/MTLStorageMode/shared) or [`MTLStorageMode.managed`](https://developer.apple.com/documentation/Metal/MTLStorageMode/managed)
- Can’t be accessible through pointer indexing, or include pointers to other argument buffers, in MSL

**Tier 2 Limits**

GPUs that support Tier 2 argument buffers have significantly higher limits that enable more capabilities in your app.

For Tier 2, argument buffers can be mutable so that the GPU and CPU can both modify the contents of them at any time. However, Metal may perform certain optimizations if you specify that neither the CPU nor the GPU modifies a buffer’s contents between the time Metal sets the buffer in a function’s argument table and the time Metal completes execution of the associated command buffer. Metal considers these types of argument buffers immutable. To indicate that an argument buffer is immutable and let Metal perform optimizations, set its associated [`MTLPipelineBufferDescriptor`](https://developer.apple.com/documentation/Metal/MTLPipelineBufferDescriptor)`.`[`mutability`](https://developer.apple.com/documentation/Metal/MTLPipelineBufferDescriptor/mutability) property to [`MTLMutability.immutable`](https://developer.apple.com/documentation/Metal/MTLMutability/immutable).

In MSL, you access Tier 2 argument buffers by indexing a pointer.

```metal
struct ArgumentBufferTextures {
    texture2d<float> diffuse;
    texture2d<float> specular;
};

struct ArgumentBufferMaterial {
    device ArgumentBufferTextures *textures;
};

fragment float4 exampleFragment(device ArgumentBufferMaterial & material)
{
    return material.textures[4]->diffuse.read(uint2(0));
}
```

Because you can’t copy samplers from the thread address space to the device address space, you only copy argument buffer samplers between argument buffers. For example, if you create `constexpr` samplers in shaders by default in the thread address space, you can’t assign them to buffers in the device address space.

```metal
struct ArgumentBufferSampler {
    sampler sampler0;
};

kernel void exampleKernel(device ArgumentBufferSampler *source,
                          device ArgumentBufferSampler *destination,
                          sampler sampler1) {
    constexpr sampler sampler2;

    // Metal allows device-to-device copies.
    destination->sampler0 = source->sampler0;

    // Metal doesn't allow thread-to-device copies.
    destination->sampler0 = sampler1;
    destination->sampler0 = sampler2;
}
```

---

Copyright © 2026 Apple Inc. All rights reserved. | [Terms of Use](https://www.apple.com/legal/internet-services/terms/site.html) | [Privacy Policy](https://www.apple.com/privacy/privacy-policy)
