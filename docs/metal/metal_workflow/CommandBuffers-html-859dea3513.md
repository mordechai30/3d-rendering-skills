Source: [https://developer.apple.com/library/archive/documentation/3DDrawing/Conceptual/MTLBestPracticesGuide/CommandBuffers.html](<https://developer.apple.com/library/archive/documentation/3DDrawing/Conceptual/MTLBestPracticesGuide/CommandBuffers.html>)

<a id="//apple_ref/doc/uid/TP40016642-CH29"></a>

<a id="//apple_ref/doc/uid/TP40016642-CH29-SW1"></a>



<a id="command-buffers"></a>

## Command Buffers

**Best Practice:** Submit the fewest possible command buffers per frame without underutilizing the GPU.

Command buffers are the unit of work submission in Metal; they are created by the CPU and executed by the GPU. This relationship allows you to balance CPU and GPU work by adjusting the number of command buffers submitted per frame.

Most Metal apps keep their CPU work one or two frames ahead of their GPU work by implementing triple buffering. This means that there is usually sufficient CPU work queued up to keep the GPU busy by submitting only one or two command buffers per frame (preferably one). However, if the CPU work does not keep far enough ahead of the GPU work, the GPU will starve. More frequent command buffer submissions may keep the GPU busy but may also introduce CPU stalls caused by CPU-GPU synchronization. Managing this tradeoff effectively is the key to improved performance and can be facilitated with the Metal System Trace profiling template in Instruments.

<a id="//apple_ref/doc/uid/TP40016642-CH29-DontLinkElementID_28"></a>



Note

For a complete overview of triple buffering, see the [Triple Buffering](./TripleBuffering-html-4fbf2e3432.md#//apple_ref/doc/uid/TP40016642-CH5-SW1) best practices.

<a id="next_previous"></a>

[Render Command Encoders (iOS and tvOS)](./RenderCommandEncoders-html-020cdcfdac.md#//apple_ref/doc/uid/TP40016642-CH30-SW1)

[Indirect Buffers](./IndirectBuffers-html-b9aef57fa5.md#//apple_ref/doc/uid/TP40016642-CH31-SW1)

Copyright © 2018 Apple Inc. All rights reserved.
[Terms of Use](http://www.apple.com/legal/terms/site.html) |
[Privacy Policy](http://www.apple.com/privacy/) |
[Updated: 2017-03-27](https://developer.apple.com/library/archive/documentation/3DDrawing/Conceptual/MTLBestPracticesGuide/RevisionHistory.html#//apple_ref/doc/uid/TP40016642-CH99-DontLinkElementID_50)
