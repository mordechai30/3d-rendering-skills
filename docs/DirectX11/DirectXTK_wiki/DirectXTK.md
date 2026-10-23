# Headers
Public headers are in the **Inc** folder of the distribution package.

# Namespace
All the functions in the library are in the **DirectX** C++ namespace.

```cpp
using namespace DirectX;
```

> The Xbox One exclusive application *XBoxDDSTextureLoader* functions are in the **Xbox** C++ namespace.

# Modules
* [Audio](Audio.md) - low-level audio API using XAudio2
     * [AudioEngine](AudioEngine.md), [SoundEffect](SoundEffect.md), [SoundEffectInstance](SoundEffectInstance.md), [SoundStreamInstance](SoundStreamInstance.md), [DynamicSoundEffectInstance](DynamicSoundEffectInstance.md), [WaveBank](WaveBank.md), [AudioListener](AudioListener.md), [AudioEmitter](AudioEmitter.md)
* [BufferHelpers](BufferHelpers.md) - C++ helpers for creating D3D resources from CPU data
* [CommonStates](CommonStates.md) - factory providing commonly used D3D state objects
* [DDSTextureLoader](DDSTextureLoader.md) - light-weight DDS file texture loader
* [DirectXHelpers](DirectXHelpers.md) - misc C++ helpers for D3D programming
* [Effects](Effects.md) - set of built-in shaders for common rendering tasks
     * [IEffectFactory](EffectFactory.md), [EffectFactory](EffectFactory.md), [PBREffectFactory](EffectFactory.md), [NPREffectFactory](EffectFactory.md), [DGSLEffectFactory](EffectFactory.md)
     * [IEffect](IEffect.md), [IEffectMatrices](IEffectMatrices.md), [IEffectLights](IEffectLights.md), [IEffectFog](IEffectFog.md), [IEffectSkinning](IEffectSkinning.md)
     * [AlphaTestEffect](AlphaTestEffect.md), [BasicEffect](BasicEffect.md), [DualTextureEffect](DualTextureEffect.md), [EnvironmentMapEffect](EnvironmentMapEffect.md), [SkinnedEffect](SkinnedEffect.md)
     * [NormalMapEffect](NormalMapEffect.md), [SkinnedNormalMapEffect](NormalMapEffect.md)
     * [PBREffect](PBREffect.md), [SkinnedPBREffect](PBREffect.md)
     * [NPREffect](NPREffect.md), [SkinnedNPREffect](NPREffect.md)
     * [DebugEffect](DebugEffect.md)
     * [DGSLEffect](DGSLEffect.md), [SkinnedDGSLEffect](DGSLEffect.md)
* [GamePad](GamePad.md) - gamepad controller helper using XInput or Windows.Gaming.Input
* [GeometricPrimitive](GeometricPrimitive.md) - draws basic shapes such as cubes and spheres
* [GraphicsMemory](GraphicsMemory.md) - helper for managing dynamic graphics memory allocation
* [Keyboard](Keyboard.md) - keyboard state tracking helper
* [Model](Model.md) - draws simple meshes loaded from .CMO, .SDKMESH, or .VBO files
     * [ModelMesh](ModelMesh.md), [ModelMeshPart](ModelMeshPart.md), [ModelBone](ModelBone.md)
* [Mouse](Mouse.md) - mouse helper
* [PostProcess](PostProcess.md) - set of built-in shaders for common post-processing operations
     * [BasicPostProcess](BasicPostProcess.md), [DualPostProcess](DualPostProcess.md), [ToneMapPostProcess](ToneMapPostProcess.md)
* [PrimitiveBatch](PrimitiveBatch.md) - simple and efficient way to draw user primitives
* [ScreenGrab](ScreenGrab.md) - light-weight screen shot saver
* [SimpleMath](SimpleMath.md) - simplified C++ wrapper for DirectXMath
     * [Rectangle](Rectangle.md), [Vector2](Vector2.md), [Vector3](Vector3.md), [Vector4](Vector4.md), [Matrix](Matrix.md), [Quaternion](Quaternion.md), [Plane](Plane.md), [Ray](Ray.md), [Color](Color.md), [Viewport](Viewport.md)
* [SpriteBatch](SpriteBatch.md) - simple & efficient 2D sprite rendering
* [SpriteFont](SpriteFont.md) - bitmap based text rendering
* [VertexTypes](VertexTypes.md) - structures for commonly used vertex data formats
* [WICTextureLoader](WICTextureLoader.md) - WIC-based image file texture loader
* [XboxDDSTextureLoader](XboxDDSTextureLoader.md) - DDSTextureLoader variant for Xbox One exclusive app developers

# Building
This code is designed to build with Visual Studio 2022 or later. It requires the Windows SDK (19041) or later for functionality such as the DirectXMath library and the DXGI 1.2 headers.

These components are designed to work without requiring any content from the DirectX SDK. For details, see [Where is the DirectX SDK?](https://docs.microsoft.com/windows/win32/directx-sdk--august-2009-), [Where is the DirectX SDK (2021 Edition)?](https://aka.ms/dxsdk), and [The Zombie DirectX SDK](https://aka.ms/AA4gfea).

## HLSL shaders
The required Direct3D shaders are built as headers in `Src\Shader\Compiled\*.inc` and included into the DirectXTK static library. They are automatically built by the Visual Studio project if they are not present, and cleared by a Clean. They can also be manually rebuilt using the ``CompileShaders.cmd`` script (i.e. `...\DirectXTK\Src\Shaders`)

## Dependencies

The _DirectX Tool Kit_ library assumes your binary is linking with the following system libraries:

* ``d3d11.lib``: Provides the Direct3D device creation function ``D3D11CreateDevice``
* ``dxgi.lib``: Provides the DXGI factory creation function ``CreateDXGIFactory1`` / ``CreateDXGIFactory2``
* ``dxguid.lib``: Provides COM GUID values for ``IID_ID3D11Device``, ``WKPDID_D3DDebugObjectName``, etc.
* ``windowscodecs.lib`` or ``uuid.lib``: Provides COM GUID values for WIC usage such as ``CLSID_WICImagingFactory``, ``CLSID_WICImagingFactory1``, ``CLSID_WICImagingFactory2``, etc.
* For Win32 desktop applications, ``ole32.lib``: Provides ``CoCreateInstance``. For other platforms, this export is in the umbrella library (``WindowsApps.lib``, ``onecore.lib``, etc.).

### DirectX Tool Kit for Audio
For Windows configurations of the AudioEngine class, you'll need to use ``xaudio2.lib``.

For [XAudio2Redist](https://docs.microsoft.com/windows/win32/xaudio2/xaudio2-redistributable), the [Microsoft.XAudio2.Redist](https://www.nuget.org/packages/Microsoft.XAudio2.Redist/) NuGet package provides the ``xaudio2_9redist.lib``.

### GamePad
For "Windows 10" and "Windows 11" configurations of the GamePad class that use Windows.Gaming.Input, you need ``runtimeobject.lib`` for Win32 desktop apps. For UWP apps, this is already handled with the umbrella lib ``windowsapp.lib``.

For "Windows 8.1" configurations of the GamePad class using XInput 1.4, you'll need ``xinput.lib``.

For the "Gaming.Desktop.x64" platform configuration in the Microsoft GDK, the GamePad class uses GameInput 'v0' and links to ``gameinput.lib``.

# Content pipeline
To use the Visual Studio graphics assets tools in the build system, be sure to [add them to your project](https://docs.microsoft.com/visualstudio/designers/using-3-d-assets-in-your-game-or-app).

**Note:** When adding ``.spritefont``, ``.sdkmesh``, or ``.xwb`` files to your Universal Windows Platform (UWP) or Xbox One project, you need to manually set the file properties to "Content: Yes" for all configurations to have these files included in your AppX package. ``.dds`` files, other image file formats, and ``.wav`` files are automatically detected as a media file and are included as content by default.

# Error handling
DirectXTK makes use of C++ exception handling which should be enabled by the application via the `/EHsc` compiler switch. In Visual Studio, this is set in the project settings under "C++ / Code Generation" with Enable C++ Exceptions set to "Yes (/EHsc)" for all configurations.

* [C++ Exception Handling](https://docs.microsoft.com/cpp/cpp/cpp-exception-handling)
* [How to: Break When an Exception is Thrown](https://docs.microsoft.com/visualstudio/debugger/managing-exceptions-with-the-debugger)
* [Dual-use Coding Techniques for Games](https://aka.ms/Fo3su4)
* [Resource Acquisition Is Initialization](https://wikipedia.org/wiki/Resource_Acquisition_Is_Initialization)
* [ThrowIfFailed](ThrowIfFailed.md)

_Visual Studio Express editions have limited exception handling debugging support, so consider using VS Community or Pro+ instead._

# Smart-pointers and reference counting
DirectXTK encourages and makes use of a number of smart-pointers to simplify resource lifetime tracking.

* ``std::unique_ptr`` - A smart-pointer that has exactly one 'owner' of the memory
* ``std::shared_ptr`` - A smart-pointer that tracks memory use with reference counting
* ``Microsoft::WRL::ComPtr`` - A [COM smart-pointer](ComPtr.md) for reference count management very similar to ATL's CComPtr

* [Smart Pointers (Modern C++)](https://docs.microsoft.com/cpp/cpp/smart-pointers-modern-cpp)
* [Managing the Lifetime of an Object](https://docs.microsoft.com/windows/win32/learnwin32/managing-the-lifetime-of-an-object)
* [COM Coding Practices](https://docs.microsoft.com/windows/win32/learnwin32/com-coding-practices#smartptr)
* [Reference Counting (Direct3D 10)](https://docs.microsoft.com/windows/win32/direct3d10/d3d10-graphics-programming-guide-api-features-reference-counting)

# Additional information
[Integration](Integration.md)

[Implementation](Implementation.md)
