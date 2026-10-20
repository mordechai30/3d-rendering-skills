Source: [https://developer.apple.com/documentation/xcode/validating-your-apps-metal-api-usage](<https://developer.apple.com/documentation/xcode/validating-your-apps-metal-api-usage>)

<!--
{
  "documentType" : "article",
  "framework" : "Xcode",
  "identifier" : "/documentation/Xcode/Validating-your-apps-Metal-API-usage",
  "metadataVersion" : "0.1.0",
  "role" : "article",
  "title" : "Validating your app’s Metal API usage"
}
-->

# Validating your app’s Metal API usage

Catch runtime issues in your Metal app using API Validation.

## Overview

The API Validation layer checks for code that calls the Metal API incorrectly, including errors in creating resources, encoding Metal commands, and performing other common tasks.
You can enable API Validation using the runtime diagnostics options in Xcode, or by using environment variables.

> Important: The API Validation layer has a small, but measurable, impact on CPU performance.

### Enable API Validation in Xcode

Follow these steps to enable API Validation using the runtime diagnostics options in the scheme settings:

1. In the Xcode toolbar, choose Edit Scheme from the Scheme menu.
   Alternatively, choose Product > Scheme > Edit Scheme.
   ![An Xcode screenshot that shows the Scheme menu with the Edit Scheme menu item highlighted.](<validating-your-apps-metal-api-usage/285c36d906c688163cb8b8f8.png>)
2. In the scheme action panel, select Run.
3. In the action setting tab, click Diagnostics.
4. Select API Validation to enable it, and click Close.
   ![A screenshot of the Xcode scheme editor with the API Validation option enabled and highlighted.](<validating-your-apps-metal-api-usage/ae79ba17bba7bf31f4b57c9b.png>)

Now, Xcode enables API Validation each time you run your scheme.

You can additionally use the Diagnostics tab to enable extra API Validation behaviors:

- Include load and store actions:
  You can enable this option to help debug incorrect load and store actions. It dynamically changes <doc://com.apple.documentation/documentation/Metal/MTLLoadAction/dontCare> to <doc://com.apple.documentation/documentation/Metal/MTLLoadAction/clear> to fuchsia color, and writes an alternating red and white checkerboard pattern into each render target with a store action of <doc://com.apple.documentation/documentation/Metal/MTLStoreAction/dontCare>. Use this option to debug incorrect load and store action modes or assumptions on the “don’t care” behavior.
- Log non-fatal actions:
  Enable additional logging of incorrect or suboptimal Metal usage that doesn’t prevent app execution. Use this option to further lint your Metal app.

> Note: You can also control these options through environment variables.

### Enable API Validation with environment variables

You can also enable API Validation by setting the following environment variables on your Metal app:

- MTL_DEBUG_LAYER=1:
  Enables all API Validation tests.
- MTL_DEBUG_LAYER_ERROR_MODE:
  Sets the behavior for when a debug layer error occurs.
  Possible values are `assert` (default), `ignore`, and `nslog`.
  `assert` causes the debug layer to log and then assert on error.
  `ignore` causes the debug layer to ignore errors, which may cause undefined behavior.
  `nslog` causes the debug layer to log errors using <doc://com.apple.documentation/documentation/Foundation/NSLog>, which may also cause undefined behavior.
- MTL_DEBUG_LAYER_VALIDATE_LOAD_ACTIONS=1:
  Converts any <doc://com.apple.documentation/documentation/Metal/MTLLoadAction/dontCare> to <doc://com.apple.documentation/documentation/Metal/MTLLoadAction/clear> using a fuchsia color, which you
  can use to locate and debug incorrect load action modes or assumptions on <doc://com.apple.documentation/documentation/Metal/MTLLoadAction/dontCare> behavior.
- MTL_DEBUG_LAYER_VALIDATE_STORE_ACTIONS=1:
  Writes an alternating red-and-white checkerboard into each render target with a store action of <doc://com.apple.documentation/documentation/Metal/MTLStoreAction/dontCare>,
  which you can use to debug incorrect store action modes or assumptions on <doc://com.apple.documentation/documentation/Metal/MTLStoreAction/dontCare> behavior.
- MTL_DEBUG_LAYER_VALIDATE_UNRETAINED_RESOURCES:
  This option takes a bitfield of modes to enable.
  The default is 0x1. The bitfield values are:
  - 0x1:
    Enabling this flag causes the command buffer to tag any objects bound to it, which the system doesn’t retain internally.
    This makes Metal Validation raise an error if the system deallocates a tagged object before the command buffer completes.
  - 0x2:
    Enabling this flag causes the command buffer to tag objects that it internally retains.
    This flag is generally unnecessary because the system can’t deallocate an object while the command buffer itself isn’t complete.
  - 0x4:
    Enabling this flag causes the system to treat deallocated tagged objects as errors even before committing the command buffer.
    This leads to a more immediate error (for example, in the call stack of the deallocation), which is more debuggable than at commit.
- MTL_DEBUG_LAYER_WARNING_MODE:
  Sets the behavior for when a debug layer warning occurs.
  Possible values are `assert`, `ignore` (default), `nslog`, and `oslog`.
  `assert` causes the debug layer to log and then assert on warning.
  `ignore` causes the debug layer to ignore warnings.
  `nslog` causes the debug layer to log warnings using <doc://com.apple.documentation/documentation/Foundation/NSLog>.
  `oslog` causes the debug layer to log warnings using <doc://com.apple.documentation/documentation/os/os_log>.

For a complete list of settings, run `man MetalValidation` in Terminal.

> Note: API Validation only checks unretained resource references from instances of <doc://com.apple.documentation/documentation/Metal/MTLCommandBuffer> and not from <doc://com.apple.documentation/documentation/Metal/MTL4CommandBuffer>.

---

Copyright &copy; 2026 Apple Inc. All rights reserved. | [Terms of Use](https://www.apple.com/legal/internet-services/terms/site.html) | [Privacy Policy](https://www.apple.com/privacy/privacy-policy)