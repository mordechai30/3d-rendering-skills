Source: [https://developer.apple.com/library/archive/documentation/3DDrawing/Conceptual/MTLBestPracticesGuide/PersistentObjects.html](<https://developer.apple.com/library/archive/documentation/3DDrawing/Conceptual/MTLBestPracticesGuide/PersistentObjects.html>)

<a id="//apple_ref/doc/uid/TP40016642-CH4"></a>

<a id="//apple_ref/doc/uid/TP40016642-CH4-SW1"></a>



<a id="//apple_ref/doc/uid/TP40016642-CH3"></a>

<a id="//apple_ref/doc/uid/TP40016642-CH3-SW1"></a>



<a id="persistent-objects"></a>

## Persistent Objects

**Best Practice:** Create persistent objects early and reuse them often.

The Metal framework provides protocols to manage persistent objects throughout the lifetime of your app. These objects are expensive to create but are usually initialized once and reused often. You do not need to create these objects at the beginning of every render or compute loop.

<a id="//apple_ref/doc/uid/TP40016642-CH4-DontLinkElementID_12"></a>



<a id="initialize-your-device-and-command-queue-first"></a>

### Initialize Your Device and Command Queue First

Call the `MTLCreateSystemDefaultDevice` function at the start of your app to obtain the default system device. Next, call the `newCommandQueue` or `newCommandQueueWithMaxCommandBufferCount:` method to create a command queue for executing GPU instructions on that device.

All apps should create only one `MTLDevice` object per GPU and reuse it for all your Metal work on that GPU. Most apps should create only one `MTLCommandQueue` object per GPU, though you may want more if each command queue represents different Metal work (for example, non-real-time compute processing and real-time graphics rendering).

<a id="//apple_ref/doc/uid/TP40016642-CH4-DontLinkElementID_43"></a>



Note

Some macOS devices feature multiple GPUs. If you need to work with multiple GPUs, call the `MTLCopyAllDevices` function to obtain an array of available devices. Create and retain at least one command queue for each GPU you use.

<a id="//apple_ref/doc/uid/TP40016642-CH4-DontLinkElementID_13"></a>



<a id="compile-your-functions-and-build-your-library-at-build-time"></a>

### Compile Your Functions and Build Your Library at Build Time

For an overview of compiling your functions and building your library at build time, see the [Functions and Libraries](./FunctionsandLibraries-html-0c595d844f.md#//apple_ref/doc/uid/TP40016642-CH24-SW1) best practices.

At runtime, use the `MTLLibrary` and `MTLFunction` objects to access your library of graphics and compute functions. Avoid building your library at runtime or fetching functions during a render or compute loop.

If you need to configure multiple render or compute pipelines, reuse `MTLFunction` objects whenever possible. You can release `MTLLibrary` and `MTLFunction` objects after building all render and compute pipelines that depend on them.

<a id="//apple_ref/doc/uid/TP40016642-CH4-DontLinkElementID_14"></a>



<a id="build-your-pipelines-once-and-reuse-them-often"></a>

### Build Your Pipelines Once and Reuse Them Often

Building a programmable pipeline involves an expensive evaluation of GPU state. You should build `MTLRenderPipelineState` and `MTLComputePipelineState` objects only once, then reuse them for every new render or compute command encoder you create. Do not build new pipelines for new command encoders. For an overview of building multiple pipelines asynchronously, see the [Pipelines](./Pipelines-html-0ca97afd3b.md#//apple_ref/doc/uid/TP40016642-CH25-SW2) best practices.

<a id="//apple_ref/doc/uid/TP40016642-CH4-DontLinkElementID_44"></a>



Note

In addition to render and compute pipelines, you may optionally create `MTLDepthStencilState` and `MTLSamplerState` objects that encapsulate depth, stencil, and sampler state. These objects are less expensive but should also be created only once and reused often.

<a id="//apple_ref/doc/uid/TP40016642-CH4-DontLinkElementID_15"></a>



<a id="allocate-resource-storage-up-front"></a>

### Allocate Resource Storage Up Front

Resource data may be static or dynamic and accessed at various stages throughout the lifetime of your app. However, the `MTLBuffer` and `MTLTexture` objects that allocate memory for this data should be created as early as possible. After these objects are created, the resource properties and storage allocation are immutable, but the data itself is not; you can update the data whenever necessary.

Reuse `MTLBuffer` and `MTLTexture` objects as much as possible, particularly for static data. Avoid creating new resources during a render or compute loop, even for dynamic data. For further information about buffers and textures, see the [Resource Management](#//apple_ref/doc/uid/TP40016642-CH3-SW1) and [Triple Buffering](./TripleBuffering-html-4fbf2e3432.md#//apple_ref/doc/uid/TP40016642-CH5-SW1) best practices.

<a id="next_previous"></a>

[Fundamental Concepts](https://developer.apple.com/library/archive/documentation/3DDrawing/Conceptual/MTLBestPracticesGuide/index.html#//apple_ref/doc/uid/TP40016642-CH27-SW1)

[Resource Options](./ResourceOptions-html-df95b8f392.md#//apple_ref/doc/uid/TP40016642-CH17-SW1)

Copyright © 2018 Apple Inc. All rights reserved.
[Terms of Use](http://www.apple.com/legal/terms/site.html) |
[Privacy Policy](http://www.apple.com/privacy/) |
[Updated: 2017-03-27](https://developer.apple.com/library/archive/documentation/3DDrawing/Conceptual/MTLBestPracticesGuide/RevisionHistory.html#//apple_ref/doc/uid/TP40016642-CH99-DontLinkElementID_50)
