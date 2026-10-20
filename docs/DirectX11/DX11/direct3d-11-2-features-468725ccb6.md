Source: [https://learn.microsoft.com/en-us/windows/win32/direct3d11/direct3d-11-2-features](<https://learn.microsoft.com/en-us/windows/win32/direct3d11/direct3d-11-2-features>)

# Direct3D 11.2 Features

The following functionality has been added in Direct3D 11.2, which is included with Windows 8.1, Windows RT 8.1, and Windows Server 2012 R2.

-   [Tiled resources](#tiled-resources)
    -   [Check tiled resources support](#check-tiled-resources-support)
-   [Extended support for WARP devices](#extended-support-for-warp-devices)
-   [Annotate graphics commands](#annotate-graphics-commands)
-   [HLSL shader linking](#hlsl-shader-linking)
    -   [Function linking graph (FLG)](#function-linking-graph-flg)
-   [Inbox HLSL compiler](#inbox-hlsl-compiler)
-   [Related topics](#related-topics)

## Tiled resources

Direct3D 11.2 lets you create tiled resources that can be thought of as large logical resources that use small amounts of physical memory. Tiled resources are useful (for example) with terrain in games, and app UI.

Tiled resources are created by specifying the [**D3D11\_RESOURCE\_MISC\_TILED**](./ne-d3d11-d3d11_resource_misc_flag-f85f09a16f.md) flag. To work with tiled resource, use these API:

-   [**ID3D11Device2::GetResourceTiling**](./nf-d3d11_2-id3d11device2-getresourcetiling-de5f1c761e.md)
-   [**ID3D11DeviceContext2::UpdateTiles**](./nf-d3d11_2-id3d11devicecontext2-updatetiles-5bdb764d7b.md)
-   [**ID3D11DeviceContext2::UpdateTileMappings**](./nf-d3d11_2-id3d11devicecontext2-updatetilemappings-66938b64dd.md)
-   [**ID3D11DeviceContext2::CopyTiles**](./nf-d3d11_2-id3d11devicecontext2-copytiles-654a6960f5.md)
-   [**ID3D11DeviceContext2::CopyTileMappings**](./nf-d3d11_2-id3d11devicecontext2-copytilemappings-d3fe099f4a.md)
-   [**ID3D11DeviceContext2::ResizeTilePool**](./nf-d3d11_2-id3d11devicecontext2-resizetilepool-9c452c8c16.md)
-   [**ID3D11DeviceContext2::TiledResourceBarrier**](./nf-d3d11_2-id3d11devicecontext2-tiledresourcebarrier-f9bb1c3484.md)
-   **D3D11\_DEBUG\_FEATURE\_DISABLE\_TILED\_RESOURCE\_MAPPING\_TRACKING\_AND\_VALIDATION** flag with [**ID3D11Debug::SetFeatureMask**](./nf-d3d11sdklayers-id3d11debug-setfeaturemask-f6b469fa48.md)

For more info about tiled resources, see [Tiled resources](./tiled-resources-8d4a7f2d4e.md).

### Check tiled resources support

Before you use tiled resources, you need to find out if the device supports tiled resources. Here's how you check for support for tiled resources:


```C++
HRESULT hr = D3D11CreateDevice(
    nullptr,                    // Specify nullptr to use the default adapter.
    D3D_DRIVER_TYPE_HARDWARE,   // Create a device using the hardware graphics driver.
    0,                          // Should be 0 unless the driver is D3D_DRIVER_TYPE_SOFTWARE.
    creationFlags,              // Set debug and Direct2D compatibility flags.
    featureLevels,              // List of feature levels this app can support.
    ARRAYSIZE(featureLevels),   // Size of the list above.
    D3D11_SDK_VERSION,          // Always set this to D3D11_SDK_VERSION for Windows Store apps.
    &device,                    // Returns the Direct3D device created.
    &m_d3dFeatureLevel,         // Returns feature level of device created.
    &context                    // Returns the device immediate context.
    );

if (SUCCEEDED(hr))
{
    D3D11_FEATURE_DATA_D3D11_OPTIONS1 featureData;
    DX::ThrowIfFailed(
        device->CheckFeatureSupport(D3D11_FEATURE_D3D11_OPTIONS1, &featureData, sizeof(featureData))
        );

    m_tiledResourcesTier = featureData.TiledResourcesTier;
}
```



## Extended support for WARP devices

Direct3D 11.2 extends support for [WARP](./overviews-direct3d-11-devices-create-warp-1c4142d50e.md) devices, which you create by passing [**D3D\_DRIVER\_TYPE\_WARP**](./ne-d3dcommon-d3d_driver_type-24df852fcc.md) in the *DriverType* parameter of [**D3D11CreateDevice**](./nf-d3d11-d3d11createdevice-fbcd3f07e1.md). The WARP software renderer in Direct3D 11.2 adds full support for Direct3D [feature level](./overviews-direct3d-11-devices-downlevel-intro-f595280e88.md) 11\_1, including [tiled resources](#tiled-resources), [**IDXGIDevice3::Trim**](/windows/desktop/api/dxgi1_3/nf-dxgi1_3-idxgidevice3-trim), shared BCn surfaces, minblend, and map default. [Double](./ns-d3d11-d3d11_feature_data_doubles-9388da963d.md) support in HLSL shaders has also been enabled along with support for 16x MSAA.

## Annotate graphics commands

Direct3D 11.2 lets you annotate graphics commands with these API:

-   [**ID3D11DeviceContext2::IsAnnotationEnabled**](./nf-d3d11_2-id3d11devicecontext2-isannotationenabled-66ad76dcf4.md)
-   [**ID3D11DeviceContext2::BeginEventInt**](./nf-d3d11_2-id3d11devicecontext2-begineventint-c35e257de4.md)
-   [**ID3D11DeviceContext2::SetMarkerInt**](./nf-d3d11_2-id3d11devicecontext2-setmarkerint-6f4ea93740.md)
-   [**ID3D11DeviceContext2::EndEvent**](./nf-d3d11_2-id3d11devicecontext2-endevent-dfcbd1a058.md)

## HLSL shader linking

Windows 8.1 adds separate compilation and linking of HLSL shaders, which allows graphics programmers to create precompiled HLSL functions, package them into libraries, and link them into full shaders at run-time. This is essentially an equivalent of C/C++ separate compilation, libraries, and linking, and it allows programmers to compose precompiled HLSL code when more information becomes available to finalize the computation. For more info about how to use shader linking, see [Using shader linking](/windows/desktop/direct3dhlsl/using-shader-linking).

Complete these steps to create a final shader using dynamic linkage at run time.

**To create and use shader linking**

1.  Create a [**ID3D11Linker**](./nn-d3d11shader-id3d11linker-e266086291.md) linker object, which represents a linking context. A single context can't be used to produce multiple shaders; a linking context is used to produce a single shader and then the linking context is thrown away.
2.  Use [**D3DLoadModule**](/windows/desktop/api/d3dcompiler/nf-d3dcompiler-d3dloadmodule) to load and set libraries from their library blobs.
3.  Use [**D3DLoadModule**](/windows/desktop/api/d3dcompiler/nf-d3dcompiler-d3dloadmodule) to load and set an entry shader blob, or create an [FLG shader](#function-linking-graph-flg).
4.  Use [**ID3D11Module**](./nn-d3d11shader-id3d11module-bb418f4c7d.md)::[**CreateInstance**](./nf-d3d11shader-id3d11module-createinstance-da49d96fa4.md) to create [**ID3D11ModuleInstance**](./nn-d3d11shader-id3d11moduleinstance-3f6f260066.md) objects, then call functions on these objects to rebind resources to their final slots.
5.  Add the libraries to the linker, then call [**ID3D11Linker**](./nn-d3d11shader-id3d11linker-e266086291.md)::[**Link**](./nf-d3d11shader-id3d11linker-link-0ee69e7094.md) to produce final shader byte code that can then be loaded and used in the runtime just like a fully precompiled and linked shader.

### Function linking graph (FLG)

Windows 8.1 also adds the Function Linking Graph (FLG). You can use FLG to construct shaders that consist of a sequence of precompiled function invocations that pass values to each other. When using the FLG, there is no need to write HLSL and invoke the HLSL compiler. Instead, the shader structure is specified programmatically using C++ API calls. FLG nodes represent input and output signatures and invocations of precompiled library functions. The order of registering the function-call nodes defines the sequence of invocations. The input signature node must be specified first, while the output signature node must be specified last. FLG edges define how values are passed from one node to another. The data types of passed values must be the same; there is no implicit type conversion. Shape and swizzling rules follow the HLSL behavior and values can only be passed forward in this sequence. For info on the FLG API, see [**ID3D11FunctionLinkingGraph**](./nn-d3d11shader-id3d11functionlinkinggraph-78c70d4712.md).

## Inbox HLSL compiler

The HLSL compiler is now inbox on Windows 8.1 and later. Now, most APIs for shader programming can be used in Windows Store apps that are built for Windows 8.1 and later. Many APIs for shader programming couldn't be used in Windows Store apps that were built for Windows 8; the reference pages for these APIs were marked with a note. But some shader APIs (for example, [**D3DCompileFromFile**](/windows/desktop/direct3dhlsl/d3dcompilefromfile)) can still only be used to develop Windows Store apps, and not in apps that you submit to the Windows Store; the reference pages for these APIs are still marked with a note.

## Related topics

<dl> <dt>

[What's new in Direct3D 11](./dx-graphics-overviews-introduction-99897347f0.md)
</dt> </dl>