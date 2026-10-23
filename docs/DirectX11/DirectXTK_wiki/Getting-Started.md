This is the _Getting Started_ tutorial for _DirectX Tool Kit_ which introduces the reader to using the DirectX Tool Kit with DirectX 11 in C++. This takes the form of a series of tutorial lessons for introducing the various functional parts of the tool kit. If you are just looking for basic integration instructions, see [Adding to a VS solution](DirectXTK.md#adding-to-a-vs-solution).

> If you are looking to use DirectX 12 and are already familiar with Direct3D 11, the place to start is the _DirectX Tool Kit for DirectX 12_ [tutorials](https://github.com/Microsoft/DirectXTK12/wiki/Getting-Started). Keep in mind that DirectX 12 is an expert API which builds on knowing the ins & outs of DirectX 11, and can be an unforgiving API to developers new to Direct3D or graphics in general.


# Background
This tutorial assumes the reader is familiar with the basics of C++ programming using Microsoft Visual C++, including writing code, building applications, and basic debugging. Coding conventions here will make use of C++11 language features such as ``nullptr``, ``auto``, ranged-based ``for`` loops, simple _lambdas_  (aka anonymous functions), the standard smart-pointer ``std::unique_ptr`` / ``std::make_unique<T>()``, and ``std::function<>``. Familiarity with the Standard C++ Library ``std::wstring`` and the ``std::vector`` container are required as well.

* [Welcome back to C++ - Modern C++](https://docs.microsoft.com/cpp/cpp/welcome-back-to-cpp-modern-cpp)
* [C++ Language and Standard Libraries](https://docs.microsoft.com/cpp/cpp/c-cpp-language-and-standard-libraries)
* [Tools for Visual C++ Development](https://docs.microsoft.com/cpp/ide/ide-and-tools-for-visual-cpp-development)
* [Smart Pointers](https://docs.microsoft.com/cpp/cpp/smart-pointers-modern-cpp)
* [ComPtr](ComPtr.md)

> If you are more comfortable with C#, then you should consider [SharpDX](https://github.com/sharpdx/SharpDX/) and [read this blog post](https://devblogs.microsoft.com/dotnet/choose-a-net-game-engine/).

This tutorial does not assume prior experience with Direct3D, but the reader should be familiar with the basic graphics concepts for DirectX or OpenGL. That said, you can get a long way using _DirectX Tool Kit_ without much in the way of graphics experience. You may also find it useful to review the _Programming Guide for Direct3D 11_ on [Microsoft Docs](https://docs.microsoft.com/windows/win32/direct3d11/dx-graphics-overviews).

* [Getting Started with Direct3D 11](https://walbourn.github.io/getting-started-with-direct3d-11/)
* [Migrating to Direct3D 11](https://docs.microsoft.com/windows/win32/direct3d11/d3d11-programming-guide-migrating)

> Note that Direct3D 11 and _DirectX Tool Kit_ are not Windows Runtime (aka "WinRT") components, so we do not make use of the C++/CX language extensions (a.k.a. ``/ZW`` switch) or C++/WinRT language projections, although it is compatible with both of those programming models. _DirectX Tool Kit_ is a 'pure' C++ library, which is why it's not directly usable by Visual Basic, C# or HTML+JavaScript applications.

# Error handling
One thing that many C++ developers, particularly game developers, may not be all that familiar with is "C++ Exception Handling". This is distinct from "Structured Exception Handling" (SEH) which some developers have seen in the past, and can leave an unfavorable impression of C++ EH. On both ARM and x64 native platforms, C++ EH is very efficient, although the x86 32-bit implementation does have some quirks. In any case, _DirectX Tool Kit_ uses C++ Exception Handling for most error conditions, just as the Standard Template Library (STL) does and the standard behavior of the operator ``new``.

* [Errors and Exception Handling](https://docs.microsoft.com/cpp/cpp/errors-and-exception-handling-modern-cpp)
* [C++ Exception Handling](https://docs.microsoft.com/cpp/cpp/cpp-exception-handling)
* [Exception Handling (Debugging)](https://docs.microsoft.com/visualstudio/debugger/managing-exceptions-with-the-debugger)
* [ThrowIfFailed](ThrowIfFailed.md)

For debugging exceptions thrown by the _DirectX Tool Kit_, you should enable the checkbox next to ``std::exception`` in the Visual Studio Exception Settings dialog (_Debug_ -> _Windows_ -> _Exception Settings_). It's not on by default. Then select the "C++ Exceptions" line, right-click and select the <kbd>+</kbd> button, and type ``DirectX::com_exception`` to add that one. If working with the [Direct3D VS Game templates](https://github.com/walbourn/directx-vs-templates) you should do this once more typing ``DX::com_exception``.

![Exception Settings](images/DebugExcept.PNG)

> For some more detail on how the Visual Studio debugger deals with exceptions, read [this](https://devblogs.microsoft.com/devops/understanding-exceptions-while-debugging-with-visual-studio/) blog post.

# Audience
These tutorials are written with game development in mind as the target application since games are an excellent fit for the 'immersive DirectX app' model. Keep in mind, however, that the majority of the functionality in the _DirectX Tool Kit_ is applicable to DirectX graphics programming in general for both game and non-game applications.

# System requirements
The DirectX Tool Kit for DirectX 11 tutorials assume you are using Windows 8.1, Windows 10 or Windows 11. The *DirectX Tool Kit* supports ``D3D_FEATURE_LEVEL_9_1`` Direct3D hardware feature level or greater. Any use of 32-bit index buffers (``DXGI_FORMAT_R32_UINT``) requires at least ``D3D_FEATURE_LEVEL_9_2``.

A few features such as [DebugEffect](DebugEffect.md), [DGSLEffect](DGSLEffect.md), [NormalMapEffect](NormalMapEffect.md), [PBREffect](PBREffect.md), [PostProcess](PostProcess.md), and dual-parabolic environment maps require ``D3D_FEATURE_LEVEL_10_0`` or better.

> Older versions of the tool kit supported Windows phone 8 and Windows Vista SP2 with KB971644.

# Software setup
For learning purposes, these instructions are going to focus on the following setup:

* VS 2022 or VS 2026 Community, Professional, Premium, or Ultimate
* Windows 11 SDK ([22000](https://walbourn.github.io/windows-sdk-for-windows-11/) is the minimum supported version)
* Windows 8.1, Windows 10 (May 2020 Update a.k.a. Version 2004 or later is recommended), or Windows 11.

We will be using a Win32 desktop application project template, but all these techniques and APIs apply to Universal Windows Platform apps and Xbox as well.

> There is no need to install the legacy DirectX SDK to use DirectX Tool Kit. The DirectX SDK is deprecated and you should not use it per [Microsoft Docs](https://docs.microsoft.com/windows/win32/directx-sdk--august-2009-). See [this blog post](https://aka.ms/dxsdk), [The Zombie DirectX SDK](https://walbourn.github.io/the-zombie-directx-sdk/), [DirectX SDK Samples Catalog](https://walbourn.github.io/directx-sdk-samples-catalog/), and [DirectX SDK Tools Catalog](https://walbourn.github.io/directx-sdk-tools-catalog/).

## Visual Studio 2022 / 2026
When using the [new lightweight installer](https://devblogs.microsoft.com/cppblog/the-lightweight-visual-studio-15-installer/) be sure to select the appropriate workloads:

* Workload: _Game development with C++_ or _Desktop development with C++_

For UWP apps, include:

* Workload: _Universal Windows Platform development_
* Optional component: _C++ Universal Windows Platform tools_

# Samples

For a quick introduction to DirectX 11 programming, take a look at the [Introductory Graphics](https://github.com/Microsoft/Xbox-ATG-Samples#introductory-graphics) samples on [Xbox-ATG-Samples](https://github.com/Microsoft/Xbox-ATG-Samples).

* Basic drawing: *SimpleTriangle*
* Basic texturing: *SimpleTexture*
* Basic lighting: *SimpleLighting*
* DirectCompute: *SimpleCompute*
* Tessellation: *SimpleBezier*
* Instancing: *SimpleInstancing*
* Multisample Antialiasing: *SimpleMSAA*

The official samples for DirectX 11 were originally shipped in the legacy *DirectX SDK*. There is an unofficial repository of these samples available on [GitHub: directx-sdk-samples](https://github.com/walbourn/directx-sdk-samples/wiki) that have been updated to remove most of their legacy dependencies. There are a few additional DirectX 11 samples on [directx-sdk-legacy-samples](https://github.com/walbourn/directx-sdk-legacy-samples/wiki)

# Tutorials

* [The basic game loop](The-basic-game-loop.md)
* [Using DeviceResources](Using-DeviceResources.md)
* [Adding the DirectX Tool Kit](Adding-the-DirectX-Tool-Kit.md)

## Graphics

* [Sprites and textures](Sprites-and-textures.md)
* [More tricks with sprites](More-tricks-with-sprites.md)
* [Drawing text](Drawing-text.md)
* [Simple rendering](Simple-rendering.md)
* [Line drawing and anti-aliasing](Line-drawing-and-anti-aliasing.md)
* [3D shapes](3D-shapes.md)
* [Rendering a model](Rendering-a-model.md)
* [Animating using model bones](Animating-using-model-bones.md)
* [Using skinned models](Using-skinned-models.md)
* [Using advanced shaders](Using-advanced-shaders.md)
* [Multistream rendering and instancing](Multistream-rendering-and-instancing.md)
* [Creating custom shaders with DGSL](Creating-custom-shaders-with-DGSL.md)
* [Writing custom shaders](Writing-custom-shaders.md)
* [Authoring an Effect](Authoring-an-Effect.md)
* [Using HDR rendering](Using-HDR-rendering.md)
* [Physically-based rendering](Physically-based-rendering.md)

## Input

* [Game controller input](Game-controller-input.md)
* [Mouse and keyboard input](Mouse-and-keyboard-input.md)

## Math

* [Using the SimpleMath library](Using-the-SimpleMath-library.md)
* [Basic game math](Basic-game-math.md)
* [Collision detection](Collision-detection.md)
* [Picking](Picking.md)
* [Mixing SimpleMath and DirectXMath](Mixing-SimpleMath-and-DirectXMath.md)

## Audio

* [Adding the DirectX Tool Kit for Audio](Adding-the-DirectX-Tool-Kit-for-Audio.md)
* [Adding audio to your project](Adding-audio-to-your-project.md)
* [Creating and playing sounds](Creating-and-playing-sounds.md)
* [Making use of wave banks](Making-use-of-wave-banks.md)
* [Using positional audio](Using-positional-audio.md)

# Resources

[Dual-use Coding Techniques for Games](https://aka.ms/Fo3su4)

[C++ Core Guidelines](https://github.com/isocpp/CppCoreGuidelines)

# Further reading

Luna, *Introduction to 3D Game Programming with DirectX 11*, Mercury Learning & Information (March 2, 2012)

Meyers, *Effective Modern C++: 42 Specific Ways to Improve Your Use of C++11 and C++14*, O'Reilly Media (November 2014)

Varcholik, *Real-Time 3D Rendering with DirectX and HLSL: A Practical Guide to Graphics Programming*, Addison-Wesley (May 31, 2014)

Zink et al, *Practical Rendering and Computation with Direct3D 11*, A K Peters/CRC Press (July 27, 2011)
