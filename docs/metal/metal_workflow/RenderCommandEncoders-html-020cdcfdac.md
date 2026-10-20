Source: [https://developer.apple.com/library/archive/documentation/3DDrawing/Conceptual/MTLBestPracticesGuide/RenderCommandEncoders.html](<https://developer.apple.com/library/archive/documentation/3DDrawing/Conceptual/MTLBestPracticesGuide/RenderCommandEncoders.html>)

<a id="//apple_ref/doc/uid/TP40016642-CH30"></a>

<a id="//apple_ref/doc/uid/TP40016642-CH30-SW1"></a>



<a id="render-command-encoders-ios-and-tvos"></a>

## Render Command Encoders (iOS and tvOS)

**Best Practice:** Merge render command encoders when possible.

Eliminating unnecessary render command encoders reduces memory bandwidth and increases performance. You can achieve these goals by merging render command encoders into a single rendering pass, when possible. To determine whether two render command encoders are merge-compatible or not, you must carefully evaluate their render targets, load and store actions, relationships, and dependencies. The simplest criteria for two merge-compatible render command encoders, `RCE1` and `RCE2`, are as follows:

- `RCE1` and `RCE2` are created in the same frame.
- `RCE1` and `RCE2` are created from the same command buffer.
- `RCE1` is created before `RCE2`.
- `RCE2` shares the same render targets as `RCE1`.
- `RCE2` does not sample from any render targets in `RCE1`.
- `RCE1`’s render target store actions are either `Store` or `DontCare`, and `RCE2`’s render target load actions are either `Load` or `DontCare`.
- No other render command encoders have been created between `RCE1` and `RCE2`.

If these criteria are met, `RCE1` and `RCE2` can be merged into a single render command encoder, `RCEM`, as shown in Figure 10-1.

<a id="//apple_ref/doc/uid/TP40016642-CH30-SW2"></a>

**Figure 10-1**A simple render command encoder merge
![image: ../Art/CommandGeneration_SimpleMerge.pdf](<RenderCommandEncodershtml/9bc07f2c857b24e61e268810.png>)

Additionally, if `RCE1` can merge with a render command encoder created before it (`RCE0`) and `RCE2` can merge with a render command encoder created after it (`RCE3`), then `RCE0`, `RCE1`, `RCE2`, and `RCE3` can all be merged.

The following sections provide guidelines for evaluating merge compatibility between render command encoders, assuming all other criteria are met.

<a id="//apple_ref/doc/uid/TP40016642-CH30-DontLinkElementID_45"></a>



Note

The details of your rendering passes are specific to your app; therefore, this guide cannot provide specific advice for how to merge a particular set of render command encoders. Render command encoders are merged manually; there is no Metal API that automatically performs a merger for you. Most mergers are accomplished by coalescing draw calls, vertex or fragment functions, or render targets. Some mergers may even be accomplished with programmable blending, as shown in the *[MetalDeferredLighting](https://developer.apple.com/library/archive/samplecode/MetalDeferredLighting/Introduction/Intro.html#//apple_ref/doc/uid/TP40014630)* sample.

The number of render targets in a merged command encoder may not exceed the limits documented in [Metal Feature Sets](https://developer.apple.com/metal/feature-sets/).

<a id="//apple_ref/doc/uid/TP40016642-CH30-DontLinkElementID_16"></a>



<a id="evaluate-rendering-pass-order"></a>

### Evaluate Rendering Pass Order

Some apps may begin encoding into a render command encoder (`RCE1`) and prematurely end the initial rendering pass if they require additional dynamic data to proceed. The dynamic data is then generated in a separate rendering pass with a second render command encoder (`RCE2`). The initial rendering pass then continues with a third render command encoder (`RCE3`). Figure 10-2 shows this inefficient order, including the separated render command encoders.

<a id="//apple_ref/doc/uid/TP40016642-CH30-SW3"></a>

**Figure 10-2**An inefficient order of rendering passes
![image: ../Art/CommandGeneration_InefficientOrder.pdf](<RenderCommandEncodershtml/a0b633f87da23f843292c2bd.png>)

If `RCE2` does not depend on `RCE1`, then `RCE2` doesn’t need to be encoded after `RCE1`. Encoding `RCE2` first allows `RCE1` and `RCE3` to be merged into `RCEM` because they represent the same rendering pass, and their dynamic data dependencies are guaranteed to be available at the start of the rendering pass. Figure 10-3 shows this improved order, including the merged render command encoders.

<a id="//apple_ref/doc/uid/TP40016642-CH30-SW4"></a>

**Figure 10-3**An improved order of rendering passes
![image: ../Art/CommandGeneration_ImprovedOrder.pdf](<RenderCommandEncodershtml/f9daa3e2859db50d647f10c0.png>)

<a id="//apple_ref/doc/uid/TP40016642-CH30-DontLinkElementID_17"></a>



<a id="evaluate-sampling-dependencies"></a>

### Evaluate Sampling Dependencies

Render command encoders cannot be merged if there are any sampling dependencies between them. For render command encoders that share the same render targets, these dependencies may be introduced by additional render command encoders in between them, as shown in Figure 10-4.

<a id="//apple_ref/doc/uid/TP40016642-CH30-SW5"></a>

**Figure 10-4**Sampling dependencies between render command encoders
![image: ../Art/CommandGeneration_SampleDependencies.pdf](<RenderCommandEncodershtml/da7aeb17507c39923e7d052f.png>)

`RCE1` and `RCE3` share the same render targets, `RT1`, `RT2`, and `RT3`. Furthermore, the actions between `RCE1` and `RCE3` indicate a continuation of a rendering pass. However, these render command encoders cannot be merged due to the sampling dependencies introduced by `RCE2`. `RCE2` renders to a separate render target, `RT4`, which is sampled by `RCE3`. Additionally, `RCE2` samples `RT3` after it is rendered by `RCE1`. These sampling dependencies define a strict rendering pass order that prevents merging these render command encoders.

<a id="//apple_ref/doc/uid/TP40016642-CH30-DontLinkElementID_18"></a>



<a id="evaluate-actions-between-rendering-passes"></a>

### Evaluate Actions Between Rendering Passes

The store and load actions between render command encoder render targets are not as important as other criteria, but there are a few notable cases where additional consideration is due. Use the following guidelines to further understand merge compatibility between render command encoders `RCE1` and `RCE2`, based on their shared render targets:

- If the store action in `RCE1` is `Store` and the load action in `RCE2` is `Load`, the render target is merge-compatible and is typically continuing a rendering pass.
- If the store action in `RCE1` is `DontCare` and the load action in `RCE2` is `DontCare`, the render target is merge-compatible and is typically being used as an intermediary resource.
- If the load action in `RCE2` is `Clear`, the render target is merge-compatible if a primitive clear operation can be performed in the merged render command encoder by first rendering clear values into a display-aligned quad.

<a id="//apple_ref/doc/uid/TP40016642-CH30-DontLinkElementID_46"></a>



Note

For advice on choosing appropriate load and store actions for a particular render target, see the [Load and Store Actions](./LoadandStoreActions-html-cd3d663642.md#//apple_ref/doc/uid/TP40016642-CH20-SW1) best practices.

<a id="next_previous"></a>

[Load and Store Actions](./LoadandStoreActions-html-cd3d663642.md#//apple_ref/doc/uid/TP40016642-CH20-SW1)

[Command Buffers](./CommandBuffers-html-859dea3513.md#//apple_ref/doc/uid/TP40016642-CH29-SW1)

Copyright © 2018 Apple Inc. All rights reserved.
[Terms of Use](http://www.apple.com/legal/terms/site.html) |
[Privacy Policy](http://www.apple.com/privacy/) |
[Updated: 2017-03-27](https://developer.apple.com/library/archive/documentation/3DDrawing/Conceptual/MTLBestPracticesGuide/RevisionHistory.html#//apple_ref/doc/uid/TP40016642-CH99-DontLinkElementID_50)
