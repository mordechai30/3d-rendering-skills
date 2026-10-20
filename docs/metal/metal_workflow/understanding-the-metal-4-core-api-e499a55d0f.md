Source: [https://developer.apple.com/documentation/metal/understanding-the-metal-4-core-api?language=objc](<https://developer.apple.com/documentation/metal/understanding-the-metal-4-core-api?language=objc>)

<!--
{
  "documentType" : "article",
  "framework" : "Metal",
  "identifier" : "/documentation/Metal/understanding-the-metal-4-core-api",
  "metadataVersion" : "0.1.0",
  "role" : "article",
  "title" : "Understanding the Metal 4 core API"
}
-->

# Understanding the Metal 4 core API

Discover the features and functionality in the Metal 4 foundational APIs.

## Discussion

Metal 4 improves runtime performance and memory efficiency
while making it easier to adapt your apps and games from other platforms,
such as DirectX and Vulkan.

Metal 4 introduces new types for existing concepts and several new ones, including:

- Command queues
- Command buffers
- Command encoders
- Command allocators
- Argument tables
- Texture view pools
- Next generation barriers

Metal 4 introduces several types with the `MTL4` prefix that are completely
independent from the original `MTL` types they replace, such as [`MTL4CommandQueue`](/documentation/Metal/MTL4CommandQueue) versus [`MTLCommandQueue`](/documentation/Metal/MTLCommandQueue).
Other types are common to all versions of Metal.

|Metal 4                                                                |Metal                                                                                                                                                                                                                                                   |
|-----------------------------------------------------------------------|--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
|``doc://com.apple.metal/documentation/Metal/MTL4CommandQueue``         |``doc://com.apple.metal/documentation/Metal/MTLCommandQueue``                                                                                                                                                                                           |
|``doc://com.apple.metal/documentation/Metal/MTL4CommandBuffer``        |``doc://com.apple.metal/documentation/Metal/MTLCommandBuffer``                                                                                                                                                                                          |
|``doc://com.apple.metal/documentation/Metal/MTL4RenderCommandEncoder`` |``doc://com.apple.metal/documentation/Metal/MTLRenderCommandEncoder``                                                                                                                                                                                   |
|``doc://com.apple.metal/documentation/Metal/MTL4ComputeCommandEncoder``|``doc://com.apple.metal/documentation/Metal/MTLComputeCommandEncoder``  ![](<understanding-the-metal-4-core-api/d9074f41c3478206b8b5bdac.png>) ``doc://com.apple.metal/documentation/Metal/MTLBlitCommandEncoder`` ![](<understanding-the-metal-4-core-api/d9074f41c3478206b8b5bdac.png>) ``doc://com.apple.metal/documentation/Metal/MTLAccelerationStructureCommandEncoder``|

At runtime, your app can detect whether the current system supports Metal 4.
For devices that support Metal 4, you can create an [`MTL4CommandQueue`](/documentation/Metal/MTL4CommandQueue),
otherwise, create an [`MTLCommandQueue`](/documentation/Metal/MTLCommandQueue).
The type of queue you create determines which family of types you work with.
For more information, see [Work submission](/documentation/Metal/work-submission).

You can incrementally adopt Metal 4 over time, which is convenient for larger projects.
Portions of your app can individually switch to submitting work to an
[`MTL4CommandQueue`](/documentation/Metal/MTL4CommandQueue) instance.
When applicable, an app can synchronize the work it sends to an [`MTL4CommandQueue`](/documentation/Metal/MTL4CommandQueue)
with other parts of the app that send work to [`MTLCommandQueue`](/documentation/Metal/MTLCommandQueue) instances.
For more information, see [Resource synchronization](/documentation/Metal/resource-synchronization).

### Command queues

Metal 4 introduces a new command queue protocol, [`MTL4CommandQueue`](/documentation/Metal/MTL4CommandQueue),
which reduces CPU runtime and memory overhead by sending work to the GPU when you commit a command buffer.
This means your app can submit work from any thread.
You create a Metal 4 command queue by calling an [`MTLDevice`](/documentation/Metal/MTLDevice) factory method,
such as [`makeMTL4CommandQueue()`](/documentation/Metal/MTLDevice/makeMTL4CommandQueue()).

Metal 4 command queues can commit multiple command buffers as a group.
Apps can encode subsets of GPU work to multiple command buffers —
each on a separate worker thread.
When the worker threads finish encoding to their respective command buffers,
you send the command buffers to the GPU as a whole by committing them to an [`MTL4CommandQueue`](/documentation/Metal/MTL4CommandQueue)
instance with one of its methods, such as [`commit:count:`](/documentation/Metal/MTL4CommandQueue/commit:count:).
This is similar to how you use an [`MTLParallelRenderCommandEncoder`](/documentation/Metal/MTLParallelRenderCommandEncoder),
but different in that you can also apply other types of work in addition to rendering.

You can synchronize work between command queues with an [`MTLEvent`](/documentation/Metal/MTLEvent) instance,
or synchronize work on the CPU and other Metal devices with an [`MTLSharedEvent`](/documentation/Metal/MTLSharedEvent) instance.
Events work with any combination of [`MTLCommandQueue`](/documentation/Metal/MTLCommandQueue) and [`MTL4CommandQueue`](/documentation/Metal/MTL4CommandQueue) instances.
This interoperability makes it easier for you to:

- Coordinate work between your app’s Metal 4 queues and existing Metal code.
- Transition to Metal 4 over time and incrementally adopt its features.

You can synchronize work within the same queue by adding a barrier
(see [Resource synchronization](/documentation/Metal/resource-synchronization)).

### Command buffers

Metal 4 introduces [`MTL4CommandBuffer`](/documentation/Metal/MTL4CommandBuffer), which is more efficient and works
differently than [`MTLCommandBuffer`](/documentation/Metal/MTLCommandBuffer) in the following ways:

- You create a Metal 4 command buffer by calling an [`MTLDevice`](/documentation/Metal/MTLDevice) factory method,
  such as [`makeCommandBuffer()`](/documentation/Metal/MTLDevice/makeCommandBuffer()), instead of from a queue.
- You submit a command buffer to any [`MTL4CommandQueue`](/documentation/Metal/MTL4CommandQueue) instance that belongs
  to the same device by calling one of its methods, such as [`commit:count:`](/documentation/Metal/MTL4CommandQueue/commit:count:),
  unlike [`MTLCommandBuffer`](/documentation/Metal/MTLCommandBuffer) which has its own [`commit()`](/documentation/Metal/MTLCommandBuffer/commit()) method.
- You can reuse and repurpose each command buffer indefinitely by starting over,
  encoding new commands, and committing it again, instead of allocating a new buffer.
- Unlike the default behavior of [`MTLCommandBuffer`](/documentation/Metal/MTLCommandBuffer), you may need to consider
  a resource’s retain count because each [`MTL4CommandBuffer`](/documentation/Metal/MTL4CommandBuffer) instance doesn’t
  create strong references to resources.
  This is similar to creating an [`MTLCommandBuffer`](/documentation/Metal/MTLCommandBuffer) with the
  [`makeCommandBufferWithUnretainedReferences()`](/documentation/Metal/MTLCommandQueue/makeCommandBufferWithUnretainedReferences()) method of an [`MTLCommandQueue`](/documentation/Metal/MTLCommandQueue).

![A diagram for the life cycle of a Metal 4 command buffer instance. Starting on the left side as a new command buffer, it moves into the next phase where it’s ready for encoding when you call its begin-with-allocator method. The next phase is when you’re ready to submit to the GPU after encoding commands into it. Committing the command buffer moves it to the next phase where the GPU runs the commands. The command buffer moves to the Finished phase after the GPU runs its commands. You can reuse the command buffer by calling its begin-with-allocator method again. The command buffer moves to an unusable phase when you call its release method, which you can call during encoding or after the GPU finishes running it.](<understanding-the-metal-4-core-api/5d607c0a3b5a48479ad42126.png>)

After committing a command buffer to a queue, you can use it again by calling its
[`beginCommandBuffer(allocator:)`](/documentation/Metal/MTL4CommandBuffer/beginCommandBuffer(allocator:)) method.
You can then encode commands to the buffer as if it were a new instance.
This is different from previous versions of Metal that require you to create a new transient,
single-use command buffer when you need to commit more work to a queue.

### Command allocators

The *command allocator* is a companion type that provides memory for command buffers.
You associate a command allocator with one command buffer at a time by calling its
[`beginCommandBuffer(allocator:)`](/documentation/Metal/MTL4CommandBuffer/beginCommandBuffer(allocator:)) method.
When you finish encoding commands to a command buffer, you can apply the allocator to
another command buffer by first calling the current command buffer’s
[`endCommandBuffer()`](/documentation/Metal/MTL4CommandBuffer/endCommandBuffer()) method and then another command buffer’s
[`beginCommandBuffer(allocator:)`](/documentation/Metal/MTL4CommandBuffer/beginCommandBuffer(allocator:)) method.

Each allocator manages the memory that your app needs to encode commands into
the command buffer that you associate with it.
Like command buffers, you create each new [`MTL4CommandAllocator`](/documentation/Metal/MTL4CommandAllocator) instance by
calling a factory method of an [`MTLDevice`](/documentation/Metal/MTLDevice),
such as [`makeCommandAllocator()`](/documentation/Metal/MTLDevice/makeCommandAllocator()).

Your app can manage the memory that it requires by using a command allocator for each frame’s work.
When the GPU finishes the work for that frame, call the
[`reset()`](/documentation/Metal/MTL4CommandAllocator/reset()) method to release the memory for reuse.

Apps can render frames by reusing a series of allocators, one for each frame it
might have in flight at the same time to begin working on the next frame.

For example, the sample code project,
[Drawing a triangle with Metal 4](/documentation/Metal/drawing-a-triangle-with-metal-4) (Hello Triangle),
works with three frames at the same time:

```objective-c
/// The number of frames the renderer works with at the same time.
#define kMaxFramesInFlight 3

/// A class that renders each of the app's video frames.
@implementation Metal4Renderer
{
    /// The Metal device the renderer draws with by sending commands to it.
    id<MTLDevice> device;

    /// A command queue the app uses to send command buffers to the Metal device.
    id<MTL4CommandQueue> commandQueue;

    /// An array of allocators that store commands for each frame
    /// while the app encodes them and the GPU runs them.
    id<MTL4CommandAllocator> commandAllocators[kMaxFramesInFlight];

    /// A command buffer the app reuses to render each frame.
    id<MTL4CommandBuffer> commandBuffer;

    // ...
}

/// Draws a frame of content to a view's drawable.
/// - Parameter view: A view with a drawable that the renderer draws into.
- (void)renderFrameToView:(nonnull MTKView *)view
{
    // ...

    // Get the next allocator in the rotation.
    uint32_t frameIndex = frameNumber % kMaxFramesInFlight;
    id<MTL4CommandAllocator> frameAllocator = commandAllocators[frameIndex];

    // Prepare to use or reuse the allocator by resetting it.
    [frameAllocator reset];

    // Prepare to use or reuse the command buffer for the frame's commands.
    [commandBuffer beginCommandBufferWithAllocator:frameAllocator];

    // ...
}
```

At any point, each in-flight frame is in a different part of its life cycle.

- The current frame is what the app displays until the GPU finishes rendering the next frame.
- Meanwhile, the GPU is rendering the first future frame from the
  most recent command buffers that the app submits to the GPU.
- The app encodes the second future frame — either on the CPU or GPU —
  and submits the frame when other frames advance to the next stage in their life cycle.

### Command encoders

The *command encoder*, [`MTL4CommandEncoder`](/documentation/Metal/MTL4CommandEncoder),
is a base protocol for other work-specific protocols that Metal provides, including:

- [`MTL4MachineLearningCommandEncoder`](/documentation/Metal/MTL4MachineLearningCommandEncoder)
- [`MTL4RenderCommandEncoder`](/documentation/Metal/MTL4RenderCommandEncoder)
- [`MTL4ComputeCommandEncoder`](/documentation/Metal/MTL4ComputeCommandEncoder)

The base command encoder protocol defines a different interface
and default behavior than its earlier counterpart, [`MTLCommandEncoder`](/documentation/Metal/MTLCommandEncoder).
The most important difference with Metal 4 encoders is that they don’t
have methods that bind individual buffers, textures, and heaps. Instead,
you configure the resource bindings in an argument table and then bind that
table to one or more pipeline stages with a command encoder.

Use [`MTL4MachineLearningCommandEncoder`](/documentation/Metal/MTL4MachineLearningCommandEncoder) to encode inference commands
that apply <doc://com.apple.documentation/documentation/CoreML> models into a command buffer,
alongside your app’s rendering and computation workloads.
For more information, see [Machine learning passes](/documentation/Metal/machine-learning-passes).

The [`MTL4RenderCommandEncoder`](/documentation/Metal/MTL4RenderCommandEncoder) protocol is the equivalent to its earlier counterpart,
[`MTLRenderCommandEncoder`](/documentation/Metal/MTLRenderCommandEncoder), and has most of the same rendering methods.
`MTL4RenderCommandEncoder` differs from `MTLRenderCommandEncoder` by removing
methods that manage resource bindings and residency sets, and methods that configure store-action options and tessellation.
Instead, `MTL4RenderCommandEncoder` gives you the ability to:

- Add a residency set to either an encoder’s command buffer,
  or the command queue you submit that command buffer to.
- Create an argument table, configure it with bindings to resources,
  and then assign it to an encoder that refers to those resources.
- Apply mesh shader techniques to replace tessellation functionality.

> Note: Store-action options (see ``doc://com.apple.metal/documentation/Metal/MTLStoreActionOptions``) aren’t available because
> they don’t apply to Apple silicon GPUs.

`MTL4RenderCommandEncoder` also supports encoding a render pass across command buffers by:

- Suspending the work at the end of one render encoder
- Resuming the work after the beginning of the next render encoder in the sequence

This technique conceptually replaces the [`MTLParallelRenderCommandEncoder`](/documentation/Metal/MTLParallelRenderCommandEncoder)
protocol and simplifies encoding a render pass in parallel with multiple threads
because each thread can have its own render encoder instead of tying all of them to a single render encoder.

The [`MTL4ComputeCommandEncoder`](/documentation/Metal/MTL4ComputeCommandEncoder) protocol is a new type that combines the
functionality of its three predecessors:

- [`MTLBlitCommandEncoder`](/documentation/Metal/MTLBlitCommandEncoder)
- [`MTLComputeCommandEncoder`](/documentation/Metal/MTLComputeCommandEncoder)
- [`MTLAccelerationStructureCommandEncoder`](/documentation/Metal/MTLAccelerationStructureCommandEncoder)

### Argument tables

Metal 4 introduces an *argument table* type that stores bindings to resources, such as data buffers, textures, and samplers, on an encoder’s behalf.
Argument tables can reduce your app’s memory footprint because:

- Metal 4 encoders don’t require memory for storing the binding tables for every resource type, at every stage.
- Each table consumes only the memory it needs to store its resource bindings.

Each [`MTL4ArgumentTable`](/documentation/Metal/MTL4ArgumentTable) instance stores a list for each resource type, which your app creates and maintains.

- Create or reuse an [`MTL4ArgumentTableDescriptor`](/documentation/Metal/MTL4ArgumentTableDescriptor) instance.
- Configure how many bindings of each type it stores by configuring its properties,
  including [`maxBufferBindCount`](/documentation/Metal/MTL4ArgumentTableDescriptor/maxBufferBindCount)
  and [`maxTextureBindCount`](/documentation/Metal/MTL4ArgumentTableDescriptor/maxTextureBindCount).
- Create an argument table by passing the descriptor instance to an [`MTLDevice`](/documentation/Metal/MTLDevice) factory method, such as [`makeArgumentTable(descriptor:)`](/documentation/Metal/MTLDevice/makeArgumentTable(descriptor:)).
- Add or update bindings to the argument table by calling its methods,
  such as [`setResource(_:bufferIndex:)`](/documentation/Metal/MTL4ArgumentTable/setResource(_:bufferIndex:))
  and [`setSamplerState(_:index:)`](/documentation/Metal/MTL4ArgumentTable/setSamplerState(_:index:)).

Assign an argument table to one or more stages of a command encoder, and then
the commands you encode with it can refer to the resources in the
argument table’s lists, such as textures and data buffers.
You can also apply a single argument table to the stages of multiple encoders at the same time.

As your app adds render or dispatch work to a command buffer by calling an encoder’s methods,
the encoder looks up the resources that the method needs from the encoder’s argument table.

The design adds flexibility for reducing your app’s CPU and memory overhead.
For example, in Metal 4 you can create a single argument table that stores bindings
to resources that apply to multiple encoders, and then reuse that argument table indefinitely.
This approach is more efficient than previous Metal encoder types, where each
encoder instance manages its own resource binding tables.
In Metal 4, the memory and runtime savings add up with each common resource
your encoders share, and each time you assign the argument table to a new encoder.

> Tip:
> Create and configure separate argument tables for your app’s disparate types of work
> so that each table only manages the common resources for similar or overlapping tasks.

### Barriers

Earlier versions of Metal support tracking data hazards for textures and heaps
you create with hazard tracking
(see the `hazardTrackingMode` property of the
[`MTLTextureDescriptor`](/documentation/Metal/MTLTextureDescriptor) and [`MTLHeapDescriptor`](/documentation/Metal/MTLHeapDescriptor) types, respectively).

In Metal 4, the framework considers all resources untracked.
You need to synchronize pipeline stages that can concurrently access a resource
if any of the shaders in these pipelines modify it.
For example, apps commonly encode a pass that writes to a common buffer that
a later pass needs to read from to do its work, such as rendering to a texture.

One of the most efficient ways to synchronize work between two or more passes is
to add a *barrier*.
A barrier tells the GPU that it needs to avoid a race condition by delaying
the start of a pipeline stage until a previous stage finishes,
so that it’s safe to access the results of that stage.
For example, if an app encodes a compute pass that produces data that a subsequent
render pass consumes in its fragment shader, the app needs to add a barrier between
the dispatch stage of the compute pass and the fragment stage of the render pass.
In that scenario, the barrier signals to the GPU that it needs to wait before
running the fragment stage of the render pass until the dispatch stage
of the compute pass finishes modifying common resources.

### Texture view pools

Metal 4 introduces the [`MTLTextureViewPool`](/documentation/Metal/MTLTextureViewPool) protocol which creates
lightweight texture views that can reduce your app’s memory footprint
compared to creating the equivalent instances of [`MTLTexture`](/documentation/Metal/MTLTexture).
Each [`MTLTexture`](/documentation/Metal/MTLTexture) instance is a heavyweight type that stores a texture’s
underlying data and metadata. Each texture also has an implicit *texture view*,
which is the default format interpretation of the texture’s underlying data.
With a texture view pool, you can create lightweight texture views that interpret
and access a texture’s underlying data with a different format than its original.
For example, you can create an [`MTLTexture`](/documentation/Metal/MTLTexture) instance with its [`pixelFormat`](/documentation/Metal/MTLTexture/pixelFormat)
equal to [`MTLPixelFormat.rgba32Uint`](/documentation/Metal/MTLPixelFormat/rgba32Uint), and then create a new texture view of
the same texture that interprets the underlying data as if its pixel format is
[`MTLPixelFormat.rg11b10Float`](/documentation/Metal/MTLPixelFormat/rg11b10Float).

Every texture view has a unique [`MTLResourceID`](/documentation/Metal/MTLResourceID), which includes:

- Texture views you create with an [`MTLTextureViewPool`](/documentation/Metal/MTLTextureViewPool) instance’s methods,
  which is the return value of those methods
- Implicit texture views that Metal assigns to each [`MTLTexture`](/documentation/Metal/MTLTexture) you create,
  which you can access with a texture’s [`gpuResourceID`](/documentation/Metal/MTLTexture/gpuResourceID) property

The resource IDs that a texture pool creates are part of a contiguous range of values that belong to that pool.
For example, for a texture view pool that has 20 texture views, you can get the resource ID
of the fifth texture view by adding `4` to the first texture view’s resource ID.
Similarly, you can get the resource ID of the last (twentieth) texture view by
adding `19` to the first texture view’s resource ID.

You can reuse a resource ID within a texture view pool, such as when you no longer need it,
by reassigning the index of that pool with another view of any texture.

A texture view pool has a contiguous range of `MTLResourceID` values that you can
manage by creating lightweight texture views, each of which gets its own resource ID.
You can repurpose any ID in the pool to another view when you no longer need the view that it currently represents.

---

Copyright &copy; 2026 Apple Inc. All rights reserved. | [Terms of Use](https://www.apple.com/legal/internet-services/terms/site.html) | [Privacy Policy](https://www.apple.com/privacy/privacy-policy)