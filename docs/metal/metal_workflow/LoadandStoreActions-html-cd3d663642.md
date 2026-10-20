Source: [https://developer.apple.com/library/archive/documentation/3DDrawing/Conceptual/MTLBestPracticesGuide/LoadandStoreActions.html](<https://developer.apple.com/library/archive/documentation/3DDrawing/Conceptual/MTLBestPracticesGuide/LoadandStoreActions.html>)

<a id="//apple_ref/doc/uid/TP40016642-CH20"></a>

<a id="//apple_ref/doc/uid/TP40016642-CH20-SW1"></a>



<a id="//apple_ref/doc/uid/TP40016642-CH19"></a>

<a id="//apple_ref/doc/uid/TP40016642-CH19-DontLinkElementID_29"></a>



<a id="load-and-store-actions"></a>

## Load and Store Actions

**Best Practice:** Set appropriate load and store actions for your render targets.

Actions performed on your Metal render targets must be configured appropriately to avoid costly and unnecessary rendering work at the start (load action) or end (store action) of a rendering pass.

<a id="//apple_ref/doc/uid/TP40016642-CH20-DontLinkElementID_8"></a>



<a id="choose-an-appropriate-load-action"></a>

### Choose an Appropriate Load Action

Use the following guidelines to determine the appropriate load action for a particular render target. These guidelines are also summarized in [Table 9-1](#//apple_ref/doc/uid/TP40016642-CH20-SW2).

- If all the render target pixels are rendered to, choose the `DontCare` action. There are no costs associated with this action, and texture data is always interpreted as undefined.
- If the previous contents of the render target do not need to be preserved and only some of its pixels are rendered to, choose the `Clear` action. This action incurs the cost of writing a clear value to each pixel.
- If the previous contents of the render target need to be preserved and only some of its pixels are rendered to, choose the `Load` action. This action incurs the cost of loading the previous contents.

<a id="//apple_ref/doc/uid/TP40016642-CH20-SW2"></a>

**Table 9-1**Choosing a render target load action

| Previous contents preserved | Pixels rendered to | Load action |
| --- | --- | --- |
| N/A | All | `DontCare` |
| No | Some | `Clear` |
| Yes | Some | `Load` |

<a id="//apple_ref/doc/uid/TP40016642-CH20-DontLinkElementID_9"></a>



<a id="choose-an-appropriate-store-action"></a>

### Choose an Appropriate Store Action

Use the following guidelines to determine the appropriate store action for a particular render target.

- If the contents of the render target do not need to be preserved, choose the `DontCare` action. There are no costs associated with this action, and texture data is always interpreted as undefined. This is a common case for depth and stencil render targets.
- If the contents of the render target need to be preserved, choose the `Store` action. This is always the case for drawables and other displayable render targets.
- If the render target is a multisample texture, refer to Table 9-2.

  <a id="//apple_ref/doc/uid/TP40016642-CH20-SW4"></a>

  **Table 9-2**Choosing a render target store action for a multisample texture

  | Multisampled contents preserved | Resolve texture specified | Resolved contents preserved | Store action |
  | --- | --- | --- | --- |
  | Yes | Yes | Yes | `storeAndMultisampleResolve` |
  | No | Yes | Yes | `MultisampleResolve` |
  | Yes | No | N/A | `Store` |
  | No | No | N/A | `DontCare` |

  <a id="//apple_ref/doc/uid/TP40016642-CH20-DontLinkElementID_39"></a>



  Note

  If you need to perform a store-and-resolve operation, always use the `storeAndMultisampleResolve` action with a single render command encoder. Some feature sets do not support the `storeAndMultisampleResolve` action; instead, a store-and-resolve operation is performed with two render command encoders by using the `Store` and `MultisampleResolve` actions.

In some cases, the store action of a particular render target may not be known up front. To defer this decision, set the temporary `unknown` value when you create a `MTLRenderPassAttachmentDescriptor` object. You must specify a known store action before you finish encoding your rendering pass, otherwise an error occurs. Setting the `unknown` value may avoid potential costs incurred by setting the `Store` store action prematurely.

<a id="//apple_ref/doc/uid/TP40016642-CH20-DontLinkElementID_10"></a>



<a id="evaluate-actions-between-rendering-passes"></a>

### Evaluate Actions Between Rendering Passes

Render targets used across multiple rendering passes should be evaluated closely for optimal combinations of store and load actions between rendering passes. Table 9-3 lists these combinations.

<a id="//apple_ref/doc/uid/TP40016642-CH20-SW3"></a>

**Table 9-3**Store and load actions between rendering passes

| First rendering pass store action | Second rendering pass load action |
| --- | --- |
| `DontCare` | One of the following actions:  `DontCare`  `Clear` |
| One of the following actions:  `Store`  `MultisampleResolve`  `storeAndMultisampleResolve` | `Load` |

<a id="next_previous"></a>

[Frame Rate (iOS and tvOS)](./FrameRate-html-5b14b85210.md#//apple_ref/doc/uid/TP40016642-CH23-SW1)

[Render Command Encoders (iOS and tvOS)](./RenderCommandEncoders-html-020cdcfdac.md#//apple_ref/doc/uid/TP40016642-CH30-SW1)

Copyright © 2018 Apple Inc. All rights reserved.
[Terms of Use](http://www.apple.com/legal/terms/site.html) |
[Privacy Policy](http://www.apple.com/privacy/) |
[Updated: 2017-03-27](https://developer.apple.com/library/archive/documentation/3DDrawing/Conceptual/MTLBestPracticesGuide/RevisionHistory.html#//apple_ref/doc/uid/TP40016642-CH99-DontLinkElementID_50)
