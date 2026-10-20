Source: [https://developer.apple.com/library/archive/documentation/3DDrawing/Conceptual/MTLBestPracticesGuide/FunctionsandLibraries.html](<https://developer.apple.com/library/archive/documentation/3DDrawing/Conceptual/MTLBestPracticesGuide/FunctionsandLibraries.html>)

<a id="//apple_ref/doc/uid/TP40016642-CH24"></a>

<a id="//apple_ref/doc/uid/TP40016642-CH24-SW1"></a>



<a id="//apple_ref/doc/uid/TP40016642-CH15"></a>

<a id="//apple_ref/doc/uid/TP40016642-CH15-DontLinkElementID_30"></a>



<a id="functions-and-libraries"></a>

## Functions and Libraries

**Best Practice:** Compile your functions and build your library at build time.

Compiling Metal shading language source code is one of the most expensive stages in the lifetime of a Metal app. Metal minimizes this cost by allowing you to compile graphics and compute functions at build time, then load them as a library at runtime.

<a id="//apple_ref/doc/uid/TP40016642-CH24-DontLinkElementID_5"></a>



<a id="build-your-library-at-build-time"></a>

### Build Your Library at Build Time

When you build your app, Xcode automatically compiles your `.metal` source files and builds them into a single default library. To obtain the resulting `MTLLibrary` object, call the `newDefaultLibrary` method once during your initial Metal setup.

<a id="//apple_ref/doc/uid/TP40016642-CH24-DontLinkElementID_37"></a>



Note

If your app has a custom build pipeline, you may prefer to use Metal’s command line utilities to build your library. For further information, see [Using Command Line Utilities to Build a Library](https://developer.apple.com/library/archive/documentation/Miscellaneous/Conceptual/MetalProgrammingGuide/Dev-Technique/Dev-Technique.html#//apple_ref/doc/uid/TP40014221-CH8-SW10) in the *[Metal Programming Guide](https://developer.apple.com/library/archive/documentation/Miscellaneous/Conceptual/MetalProgrammingGuide/Introduction/Introduction.html#//apple_ref/doc/uid/TP40014221)*.

Building your library at runtime incurs a significant performance cost. Do so *only* if your graphics and compute functions are created dynamically at runtime. In all other situations, always build your library at build time.

<a id="//apple_ref/doc/uid/TP40016642-CH24-DontLinkElementID_38"></a>



Important

The `#include` directive is not supported at runtime for user files.

<a id="//apple_ref/doc/uid/TP40016642-CH24-DontLinkElementID_6"></a>



<a id="group-your-functions-into-a-single-library"></a>

### Group Your Functions into a Single Library

Using Xcode to build a single default library is the fastest and most efficient build option. If you must use Metal’s command line utilities or runtime methods to build your library, coalesce your Metal shading language source code and group all your functions into a single library. Avoid creating multiple libraries, if possible.

<a id="next_previous"></a>

[Indirect Buffers](./IndirectBuffers-html-b9aef57fa5.md#//apple_ref/doc/uid/TP40016642-CH31-SW1)

[Pipelines](./Pipelines-html-0ca97afd3b.md#//apple_ref/doc/uid/TP40016642-CH25-SW2)

Copyright © 2018 Apple Inc. All rights reserved.
[Terms of Use](http://www.apple.com/legal/terms/site.html) |
[Privacy Policy](http://www.apple.com/privacy/) |
[Updated: 2017-03-27](https://developer.apple.com/library/archive/documentation/3DDrawing/Conceptual/MTLBestPracticesGuide/RevisionHistory.html#//apple_ref/doc/uid/TP40016642-CH99-DontLinkElementID_50)
