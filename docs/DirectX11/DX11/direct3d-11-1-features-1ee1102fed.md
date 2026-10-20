Source: [https://learn.microsoft.com/en-us/windows/win32/direct3d11/direct3d-11-1-features](<https://learn.microsoft.com/en-us/windows/win32/direct3d11/direct3d-11-1-features>)

# Direct3D 11.1 Features

The following functionality has been added in Direct3D 11.1, which is included with Windows 8, Windows RT, and Windows Server 2012. Partial support for [Direct3D 11.1](./direct3d-11-features-a062c55bb8.md) is available on Windows 7 and Windows Server 2008 R2 via the [Platform Update for Windows 7](/windows/desktop/direct3darticles/platform-update-for-windows-7), which is available through the [Platform Update for Windows 7](https://support.microsoft.com/kb/2670838).

-   [Shader tracing and compiler enhancements](#shader-tracing-and-compiler-enhancements)
-   [Direct3D device sharing](#direct3d-device-sharing)
-   [Check support of new Direct3D 11.1 features and formats](#check-support-of-new-direct3d-111-features-and-formats)
-   [Use HLSL minimum precision](#use-hlsl-minimum-precision)
-   [Specify user clip planes in HLSL on feature level 9 and higher](#specify-user-clip-planes-in-hlsl-on-feature-level-9-and-higher)
-   [Create larger constant buffers than a shader can access](#create-larger-constant-buffers-than-a-shader-can-access)
-   [Use logical operations in a render target](#use-logical-operations-in-a-render-target)
-   [Force the sample count to create a rasterizer state](#force-the-sample-count-to-create-a-rasterizer-state)
-   [Process video resources with shaders](#process-video-resources-with-shaders)
-   [Extended support for shared Texture2D resources](#extended-support-for-shared-texture2d-resources)
-   [Change subresources with new copy options](#change-subresources-with-new-copy-options)
-   [Discard resources and resource views](#discard-resources-and-resource-views)
-   [Support a larger number of UAVs](#support-a-larger-number-of-uavs)
-   [Bind a subrange of a constant buffer to a shader](#bind-a-subrange-of-a-constant-buffer-to-a-shader)
-   [Retrieve the subrange of a constant buffer that is bound to a shader](#retrieve-the-subrange-of-a-constant-buffer-that-is-bound-to-a-shader)
-   [Clear all or part of a resource view](#clear-all-or-part-of-a-resource-view)
-   [Map SRVs of dynamic buffers with NO\_OVERWRITE](/windows)
-   [Use UAVs at every pipeline stage](#use-uavs-at-every-pipeline-stage)
-   [Extended support for WARP devices](#extended-support-for-warp-devices)
-   [Use Direct3D in Session 0 processes](#use-direct3d-in-session-0-processes)
-   [Support for shadow buffer on feature level 9](#support-for-shadow-buffer-on-feature-level-9)
-   [Related topics](#related-topics)

## Shader tracing and compiler enhancements

Direct3D 11.1 lets you use shader tracing to ensure that your code is performing as intended and if it isn’t you can discover and remedy the problem. The Windows Software Development Kit (SDK) for Windows 8 contains HLSL compiler enhancements. Shader tracing and the HLSL compiler are implemented in D3dcompiler\_nn.dll.

The shader tracing API and the enhancements to the HLSL compiler consists of the following methods and functions.

-   [**ID3D11RefDefaultTrackingOptions::SetTrackingOptions**](./nf-d3d11sdklayers-id3d11refdefaulttrackingoptions-settrackingoptions-82d67ced99.md)
-   [**ID3D11RefTrackingOptions::SetTrackingOptions**](./nf-d3d11sdklayers-id3d11reftrackingoptions-settrackingoptions-da861d1716.md)
-   [**ID3D11TracingDevice::SetShaderTrackingOptions**](./nf-d3d11sdklayers-id3d11tracingdevice-setshadertrackingoptionsbytype-4eecfdeb68.md)
-   [**ID3D11TracingDevice::SetShaderTrackingOptionsByType**](./nf-d3d11sdklayers-id3d11tracingdevice-setshadertrackingoptionsbytype-4eecfdeb68.md)
-   [**ID3D11ShaderTraceFactory::CreateShaderTrace**](./nf-d3d11shadertracing-id3d11shadertracefactory-createshadertrace-a2d92607b8.md)
-   [**ID3D11ShaderTrace::TraceReady**](./nf-d3d11shadertracing-id3d11shadertrace-traceready-c928924481.md)
-   [**ID3D11ShaderTrace::ResetTrace**](./nf-d3d11shadertracing-id3d11shadertrace-resettrace-055c333598.md)
-   [**ID3D11ShaderTrace::GetTraceStats**](./nf-d3d11shadertracing-id3d11shadertrace-gettracestats-71beb743bc.md)
-   [**ID3D11ShaderTrace::PSSelectStamp**](./nf-d3d11shadertracing-id3d11shadertrace-psselectstamp-14793274f1.md)
-   [**ID3D11ShaderTrace::GetInitialRegisterContents**](./nf-d3d11shadertracing-id3d11shadertrace-getinitialregistercontents-99ef7f0e64.md)
-   [**ID3D11ShaderTrace::GetStep**](./nf-d3d11shadertracing-id3d11shadertrace-getstep-2a8884f635.md)
-   [**ID3D11ShaderTrace::GetWrittenRegister**](./nf-d3d11shadertracing-id3d11shadertrace-getwrittenregister-0efbdd3883.md)
-   [**ID3D11ShaderTrace::GetReadRegister**](./nf-d3d11shadertracing-id3d11shadertrace-getreadregister-908774159a.md)
-   [**D3DCompile2**](/windows/desktop/direct3dhlsl/d3dcompile2)
-   [**D3DCompileFromFile**](/windows/desktop/direct3dhlsl/d3dcompilefromfile)
-   [**D3DDisassemble11Trace**](/windows/desktop/direct3dhlsl/d3ddisassemble11trace)
-   [**D3DDisassembleRegion**](/windows/desktop/direct3dhlsl/d3ddisassembleregion)
-   [**D3DGetTraceInstructionOffsets**](/windows/desktop/direct3dhlsl/d3dgettraceinstructionoffsets)
-   [**D3DReadFileToBlob**](/windows/desktop/direct3dhlsl/d3dreadfiletoblob)
-   [**D3DSetBlobPart**](/windows/desktop/direct3dhlsl/d3dsetblobpart)
-   [**D3DWriteBlobToFile**](/windows/desktop/direct3dhlsl/d3dwriteblobtofile)

The D3dcompiler.lib library requires D3dcompiler\_nn.dll. This DLL is not part of Windows 8; it is in the \\bin folder of the Windows SDK for Windows 8 along with the Fxc.exe command-line version of the HLSL compiler.

> [!Note]  
> While you can use this library and DLL combination for development, you can't deploy Windows Store apps that use this combination. Therefore, you must instead compile HLSL shaders before you ship your Windows Store app. You can write HLSL compilation binaries to disk, or the compiler can generate headers with static byte arrays that contain the shader blob data. You use the [**ID3DBlob**](/previous-versions/windows/desktop/legacy/ff728743(v=vs.85)) interface to access the blob data. To develop your Windows Store app, call [**D3DCompile2**](/windows/desktop/direct3dhlsl/d3dcompile2) or [**D3DCompileFromFile**](/windows/desktop/direct3dhlsl/d3dcompilefromfile) to compile the raw HLSL source, and then feed the resulting blob data to Direct3D.

 

## Direct3D device sharing

Direct3D 11.1 enables Direct3D 10 APIs and Direct3D 11 APIs to use one underlying rendering device.

This Direct3D 11.1 feature consists of the following methods and interface.

-   [**ID3D11Device1::CreateDeviceContextState**](./nf-d3d11_1-id3d11device1-createdevicecontextstate-1ad27aa2b5.md)
-   [**ID3D11DeviceContext1::SwapDeviceContextState**](./nf-d3d11_1-id3d11devicecontext1-swapdevicecontextstate-c4ac14a1cd.md)
-   [**ID3DDeviceContextState**](./nn-d3d11_1-id3ddevicecontextstate-c30d72b7b8.md)

## Check support of new Direct3D 11.1 features and formats

Direct3D 11.1 lets you check for new features that the graphics driver might support and new ways that a format is supported on a device. Microsoft DirectX Graphics Infrastructure (DXGI) 1.2 also specifies new [**DXGI\_FORMAT**](/windows/desktop/api/dxgiformat/ne-dxgiformat-dxgi_format) values.

This Direct3D 11.1 feature consists of the following API.

-   [**ID3D11Device::CheckFeatureSupport**](./nf-d3d11-id3d11device-checkfeaturesupport-ec5826ac8e.md) with [**D3D11\_FEATURE\_DATA\_D3D11\_OPTIONS**](./ns-d3d11-d3d11_feature_data_d3d11_options-844c1460d6.md), [**D3D11\_FEATURE\_DATA\_ARCHITECTURE\_INFO**](./ns-d3d11-d3d11_feature_data_architecture_info-720b4920a8.md), [**D3D11\_FEATURE\_DATA\_D3D9\_OPTIONS**](./ns-d3d11-d3d11_feature_data_d3d9_options-2d8016c5e0.md), [**D3D11\_FEATURE\_DATA\_SHADER\_MIN\_PRECISION\_SUPPORT**](./ns-d3d11-d3d11_feature_data_shader_min_precision_support-d544fc371c.md), and [**D3D11\_FEATURE\_DATA\_D3D9\_SHADOW\_SUPPORT**](./ns-d3d11-d3d11_feature_data_d3d9_shadow_support-80f3ad6218.md) structures
-   [**ID3D11Device::CheckFormatSupport**](./nf-d3d11-id3d11device-checkformatsupport-d86099fa87.md) with [**D3D11\_FORMAT\_SUPPORT\_DECODER\_OUTPUT**](./ne-d3d11-d3d11_format_support-ffd055ef6a.md), [**D3D11\_FORMAT\_SUPPORT\_VIDEO\_PROCESSOR\_OUTPUT**](./ne-d3d11-d3d11_format_support-ffd055ef6a.md), [**D3D11\_FORMAT\_SUPPORT\_VIDEO\_PROCESSOR\_INPUT**](./ne-d3d11-d3d11_format_support-ffd055ef6a.md), [**D3D11\_FORMAT\_SUPPORT\_VIDEO\_ENCODER**](./ne-d3d11-d3d11_format_support-ffd055ef6a.md), and [**D3D11\_FORMAT\_SUPPORT2\_OUTPUT\_MERGER\_LOGIC\_OP**](./ne-d3d11-d3d11_format_support2-4c684fd980.md)

## Use HLSL minimum precision

Starting with Windows 8, graphics drivers can implement minimum precision [HLSL scalar data types](/windows/desktop/direct3dhlsl/dx-graphics-hlsl-scalar) by using any precision greater than or equal to their specified bit precision. When your HLSL minimum precision shader code is used on hardware that implements HLSL minimum precision, you use less memory bandwidth and as a result you also use less system power.

You can query for the minimum precision support that the graphics driver provides by calling [**ID3D11Device::CheckFeatureSupport**](./nf-d3d11-id3d11device-checkfeaturesupport-ec5826ac8e.md) with the [**D3D11\_FEATURE\_SHADER\_MIN\_PRECISION\_SUPPORT**](./ne-d3d11-d3d11_feature-a05a7560bc.md) value. In this **ID3D11Device::CheckFeatureSupport** call, pass a pointer to a [**D3D11\_FEATURE\_DATA\_SHADER\_MIN\_PRECISION\_SUPPORT**](./ns-d3d11-d3d11_feature_data_shader_min_precision_support-d544fc371c.md) structure that **ID3D11Device::CheckFeatureSupport** fills with the minimum precision levels that the driver supports for the pixel shader stage and for other shader stages. The returned info just indicates that the graphics hardware can perform HLSL operations at a lower precision than the standard 32-bit float precision, but doesn’t guarantee that the graphics hardware will actually run at a lower precision.

You don't need to author multiple shaders that do and don't use minimum precision. Instead, create shaders with minimum precision, and the minimum precision variables behave at full 32-bit precision if the graphics driver reports that it doesn't support any minimum precision. For more info about HLSL minimum precision, see [Using HLSL minimum precision](/windows/desktop/direct3dhlsl/using-hlsl-minimum-precision).

HLSL minimum precision shaders don't work on operating systems earlier than Windows 8.

## Specify user clip planes in HLSL on feature level 9 and higher

Starting with Windows 8, you can use the **clipplanes** function attribute in an HLSL [function declaration](/windows/desktop/direct3dhlsl/dx-graphics-hlsl-function-syntax) rather than [SV\_ClipDistance](/windows/desktop/direct3dhlsl/dx-graphics-hlsl-semantics) to make your shader work on [feature level](./overviews-direct3d-11-devices-downlevel-intro-f595280e88.md) 9\_x as well as feature level 10 and higher. For more info, see [User clip planes on feature level 9 hardware](/windows/desktop/direct3dhlsl/user-clip-planes-on-10level9).

## Create larger constant buffers than a shader can access

Direct3D 11.1 lets you create constant buffers that are larger than the maximum constant buffer size that a shader can access (4096 32-bit\*4-component constants – 64KB). Later, when you bind the buffers to the pipeline, for example, via [**PSSetConstantBuffers**](./nf-d3d11-id3d11devicecontext-pssetconstantbuffers-98291edc2d.md) or [**PSSetConstantBuffers1**](./nf-d3d11_1-id3d11devicecontext1-pssetconstantbuffers1-08130bc0fe.md), you can specify a range of buffers that the shader can access that fits within the 4096 limit.

Direct3D 11.1 updates the [**ID3D11Device::CreateBuffer**](./nf-d3d11-id3d11device-createbuffer-973d575f5e.md) method for this feature.

## Use logical operations in a render target

Direct3D 11.1 lets you use logical operations rather than blending in a render target. However, you can’t mix logic operations with blending across multiple render targets.

This Direct3D 11.1 feature consists of the following API.

-   [**ID3D11Device1::CreateBlendState1**](./nf-d3d11_1-id3d11device1-createblendstate1-e3f7303ae1.md) with [**D3D11\_LOGIC\_OP**](./ne-d3d11_1-d3d11_logic_op-de2595384b.md)

## Force the sample count to create a rasterizer state

Direct3D 11.1 lets you specify a force sample count when you create a rasterizer state.

This Direct3D 11.1 feature consists of the following API.

-   [**ID3D11Device1::CreateRasterizerState1**](./nf-d3d11_1-id3d11device1-createrasterizerstate1-3b3ce6b992.md)

> [!Note]  
>
> If you want to render with the sample count forced to 1 or greater, you must follow these guidelines:
>
> -   Don't bind depth-stencil views.
> -   Disable depth testing.
> -   Ensure the shader doesn't output depth.
> -   If you have any render-target views bound ([**D3D11\_BIND\_RENDER\_TARGET**](./ne-d3d11-d3d11_bind_flag-78d4ee3d0d.md)) and you forced the sample count to greater than 1, ensure that every render target has only a single sample.
> -   Don't operate the shader at sample frequency. Therefore, [**ID3D11ShaderReflection::IsSampleFrequencyShader**](./nf-d3d11shader-id3d11shaderreflection-issamplefrequencyshader-4c2bd11944.md) returns **FALSE**.
>
> Otherwise, rendering behavior is undefined. For info about how to configure depth-stencil, see [Configuring Depth-Stencil Functionality](./d3d10-graphics-programming-guide-depth-stencil-aa911f9076.md).

 

## Process video resources with shaders

Direct3D 11.1 lets you create views (SRV/RTV/UAV) to video resources so that Direct3D shaders can process those video resources. The format of an underlying video resource restricts the formats that the view can use. The [**DXGI\_FORMAT**](/windows/desktop/api/dxgiformat/ne-dxgiformat-dxgi_format) enumeration contains new video resource format values. These **DXGI\_FORMAT** values specify the valid view formats that you can create and how the Direct3D 11.1 runtime maps the view. You can create multiple views of different parts of the same surface, and depending on the format, the sizes of the views can differ from each other.

Direct3D 11.1 updates the following methods for this feature.

-   [**ID3D11Device::CreateShaderResourceView**](./nf-d3d11-id3d11device-createshaderresourceview-d297e652f2.md)
-   [**ID3D11Device::CreateRenderTargetView**](./nf-d3d11-id3d11device-createrendertargetview-92322868bc.md)
-   [**ID3D11Device::CreateUnorderedAccessView**](./nf-d3d11-id3d11device-createunorderedaccessview-60ef8d74a3.md)

## Extended support for shared Texture2D resources

Direct3D 11.1 guarantees that you can share Texture2D resources that you created with particular resource types and formats. To share Texture2D resources, use the [**D3D11\_RESOURCE\_MISC\_SHARED**](./ne-d3d11-d3d11_resource_misc_flag-f85f09a16f.md), [**D3D11\_RESOURCE\_MISC\_SHARED\_KEYEDMUTEX**](./ne-d3d11-d3d11_resource_misc_flag-f85f09a16f.md), or a combination of the **D3D11\_RESOURCE\_MISC\_SHARED\_KEYEDMUTEX** and [**D3D11\_RESOURCE\_MISC\_SHARED\_NTHANDLE**](./ne-d3d11-d3d11_resource_misc_flag-f85f09a16f.md) (new for Windows 8) flags when you create those resources.

Direct3D 11.1 guarantees that you can share Texture2D resources that you created with these [**DXGI\_FORMAT**](/windows/desktop/api/dxgiformat/ne-dxgiformat-dxgi_format) values:

-   DXGI\_FORMAT\_R8G8B8A8\_UNORM
-   DXGI\_FORMAT\_R8G8B8A8\_UNORM\_SRGB
-   DXGI\_FORMAT\_B8G8R8A8\_UNORM
-   DXGI\_FORMAT\_B8G8R8A8\_UNORM\_SRGB
-   DXGI\_FORMAT\_B8G8R8X8\_UNORM
-   DXGI\_FORMAT\_B8G8R8X8\_UNORM\_SRGB
-   DXGI\_FORMAT\_R10G10B10A2\_UNORM
-   DXGI\_FORMAT\_R16G16B16A16\_FLOAT

In addition, Direct3D 11.1 guarantees that you can share Texture2D resources that you created with a mipmap level of 1, array size of 1, bind flags of [**D3D11\_BIND\_SHADER\_RESOURCE**](./ne-d3d11-d3d11_bind_flag-78d4ee3d0d.md) and [**D3D11\_BIND\_RENDER\_TARGET**](./ne-d3d11-d3d11_bind_flag-78d4ee3d0d.md) combined, usage default ([**D3D11\_USAGE\_DEFAULT**](./ne-d3d11-d3d11_usage-8197affe09.md)), and only these [**D3D11\_RESOURCE\_MISC\_FLAG**](./ne-d3d11-d3d11_resource_misc_flag-f85f09a16f.md) values:

-   [**D3D11\_RESOURCE\_MISC\_SHARED**](./ne-d3d11-d3d11_resource_misc_flag-f85f09a16f.md)
-   [**D3D11\_RESOURCE\_MISC\_SHARED\_KEYEDMUTEX**](./ne-d3d11-d3d11_resource_misc_flag-f85f09a16f.md)
-   [**D3D11\_RESOURCE\_MISC\_SHARED\_NTHANDLE**](./ne-d3d11-d3d11_resource_misc_flag-f85f09a16f.md)
-   [**D3D11\_RESOURCE\_MISC\_GDI\_COMPATIBLE**](./ne-d3d11-d3d11_resource_misc_flag-f85f09a16f.md)

Direct3D 11.1 lets you share a greater variety of Texture2D resource types and formats. You can query for whether the graphics driver and hardware support extended Texture2D resource sharing by calling [**ID3D11Device::CheckFeatureSupport**](./nf-d3d11-id3d11device-checkfeaturesupport-ec5826ac8e.md) with the [**D3D11\_FEATURE\_D3D11\_OPTIONS**](./ne-d3d11-d3d11_feature-a05a7560bc.md) value. In this **ID3D11Device::CheckFeatureSupport** call, pass a pointer to a [**D3D11\_FEATURE\_DATA\_D3D11\_OPTIONS**](./ns-d3d11-d3d11_feature_data_d3d11_options-844c1460d6.md) structure. **ID3D11Device::CheckFeatureSupport** sets the **ExtendedResourceSharing** member of **D3D11\_FEATURE\_DATA\_D3D11\_OPTIONS** to **TRUE** if the hardware and driver support extended Texture2D resource sharing.

If [**ID3D11Device::CheckFeatureSupport**](./nf-d3d11-id3d11device-checkfeaturesupport-ec5826ac8e.md) returns **TRUE** in **ExtendedResourceSharing**, you can share resources that you created with these [**DXGI\_FORMAT**](/windows/desktop/api/dxgiformat/ne-dxgiformat-dxgi_format) values:

-   DXGI\_FORMAT\_R32G32B32A32\_TYPELESS
-   DXGI\_FORMAT\_R32G32B32A32\_FLOAT
-   DXGI\_FORMAT\_R32G32B32A32\_UINT
-   DXGI\_FORMAT\_R32G32B32A32\_SINT
-   DXGI\_FORMAT\_R16G16B16A16\_TYPELESS
-   DXGI\_FORMAT\_R16G16B16A16\_FLOAT
-   DXGI\_FORMAT\_R16G16B16A16\_UNORM
-   DXGI\_FORMAT\_R16G16B16A16\_UINT
-   DXGI\_FORMAT\_R16G16B16A16\_SNORM
-   DXGI\_FORMAT\_R16G16B16A16\_SINT
-   DXGI\_FORMAT\_R10G10B10A2\_UNORM
-   DXGI\_FORMAT\_R10G10B10A2\_UINT
-   DXGI\_FORMAT\_R8G8B8A8\_TYPELESS
-   DXGI\_FORMAT\_R8G8B8A8\_UNORM
-   DXGI\_FORMAT\_R8G8B8A8\_UNORM\_SRGB
-   DXGI\_FORMAT\_R8G8B8A8\_UINT
-   DXGI\_FORMAT\_R8G8B8A8\_SNORM
-   DXGI\_FORMAT\_R8G8B8A8\_SINT
-   DXGI\_FORMAT\_B8G8R8A8\_TYPELESS
-   DXGI\_FORMAT\_B8G8R8A8\_UNORM
-   DXGI\_FORMAT\_B8G8R8X8\_UNORM
-   DXGI\_FORMAT\_B8G8R8A8\_UNORM\_SRGB
-   DXGI\_FORMAT\_B8G8R8X8\_TYPELESS
-   DXGI\_FORMAT\_B8G8R8X8\_UNORM\_SRGB
-   DXGI\_FORMAT\_R32\_TYPELESS
-   DXGI\_FORMAT\_R32\_FLOAT
-   DXGI\_FORMAT\_R32\_UINT
-   DXGI\_FORMAT\_R32\_SINT
-   DXGI\_FORMAT\_R16\_TYPELESS
-   DXGI\_FORMAT\_R16\_FLOAT
-   DXGI\_FORMAT\_R16\_UNORM
-   DXGI\_FORMAT\_R16\_UINT
-   DXGI\_FORMAT\_R16\_SNORM
-   DXGI\_FORMAT\_R16\_SINT
-   DXGI\_FORMAT\_R8\_TYPELESS
-   DXGI\_FORMAT\_R8\_UNORM
-   DXGI\_FORMAT\_R8\_UINT
-   DXGI\_FORMAT\_R8\_SNORM
-   DXGI\_FORMAT\_R8\_SINT
-   DXGI\_FORMAT\_A8\_UNORM
-   DXGI\_FORMAT\_AYUV
-   DXGI\_FORMAT\_YUY2
-   DXGI\_FORMAT\_NV12
-   DXGI\_FORMAT\_NV11
-   DXGI\_FORMAT\_P016
-   DXGI\_FORMAT\_P010
-   DXGI\_FORMAT\_Y216
-   DXGI\_FORMAT\_Y210
-   DXGI\_FORMAT\_Y416
-   DXGI\_FORMAT\_Y410

If [**ID3D11Device::CheckFeatureSupport**](./nf-d3d11-id3d11device-checkfeaturesupport-ec5826ac8e.md) returns **TRUE** in **ExtendedResourceSharing**, you can share resources that you created with these features and flags:

-   [**D3D11\_USAGE\_DEFAULT**](./ne-d3d11-d3d11_usage-8197affe09.md)
-   [**D3D11\_BIND\_SHADER\_RESOURCE**](./ne-d3d11-d3d11_bind_flag-78d4ee3d0d.md)
-   [**D3D11\_BIND\_RENDER\_TARGET**](./ne-d3d11-d3d11_bind_flag-78d4ee3d0d.md)
-   [**D3D11\_RESOURCE\_MISC\_GENERATE\_MIPS**](./ne-d3d11-d3d11_resource_misc_flag-f85f09a16f.md)
-   [**D3D11\_BIND\_UNORDERED\_ACCESS**](./ne-d3d11-d3d11_bind_flag-78d4ee3d0d.md)
-   Mipmap levels (one or more levels) in the 2D texture resources (specified in the **MipLevels** member of [**D3D11\_TEXTURE2D\_DESC**](./ns-d3d11-d3d11_texture2d_desc-f26127b311.md))
-   Arrays of 2D texture resources (one or more textures) (specified in the **ArraySize** member of [**D3D11\_TEXTURE2D\_DESC**](./ns-d3d11-d3d11_texture2d_desc-f26127b311.md))
-   [**D3D11\_BIND\_DECODER**](./ne-d3d11-d3d11_bind_flag-78d4ee3d0d.md)
-   [**D3D11\_RESOURCE\_MISC\_RESTRICTED\_CONTENT**](./ne-d3d11-d3d11_resource_misc_flag-f85f09a16f.md)
-   [**D3D11\_RESOURCE\_MISC\_RESTRICT\_SHARED\_RESOURCE**](./ne-d3d11-d3d11_resource_misc_flag-f85f09a16f.md)
-   [**D3D11\_RESOURCE\_MISC\_RESTRICT\_SHARED\_RESOURCE\_DRIVER**](./ne-d3d11-d3d11_resource_misc_flag-f85f09a16f.md)

> [!Note]  
> When **ExtendedResourceSharing** is **TRUE**, you have more flexibility when you specify bind flags for sharing Texture2D resources. Not only does the graphics driver and hardware support more bind flags but also more possible combinations of bind flags. For example, you can specify just [**D3D11\_BIND\_RENDER\_TARGET**](./ne-d3d11-d3d11_bind_flag-78d4ee3d0d.md) or no bind flags, and so on.

 

Even if [**ID3D11Device::CheckFeatureSupport**](./nf-d3d11-id3d11device-checkfeaturesupport-ec5826ac8e.md) returns **TRUE** in **ExtendedResourceSharing**, you still can't share resources that you created with these features and flags:

-   [**D3D11\_BIND\_DEPTH\_STENCIL**](./ne-d3d11-d3d11_bind_flag-78d4ee3d0d.md)
-   2D texture resources in multisample antialiasing (MSAA) mode (specified with [**DXGI\_SAMPLE\_DESC**](/windows/desktop/api/dxgicommon/ns-dxgicommon-dxgi_sample_desc))
-   [**D3D11\_RESOURCE\_MISC\_RESOURCE\_CLAMP**](./ne-d3d11-d3d11_resource_misc_flag-f85f09a16f.md)
-   [**D3D11\_USAGE\_IMMUTABLE**](./ne-d3d11-d3d11_usage-8197affe09.md), [**D3D11\_USAGE\_DYNAMIC**](./ne-d3d11-d3d11_usage-8197affe09.md), or [**D3D11\_USAGE\_STAGING**](./ne-d3d11-d3d11_usage-8197affe09.md) (that is, mappable)
-   [**D3D11\_RESOURCE\_MISC\_TEXTURECUBE**](./ne-d3d11-d3d11_resource_misc_flag-f85f09a16f.md)

## Change subresources with new copy options

Direct3D 11.1 lets you use new copy flags to copy and update subresources. When you copy a subresource, the source and destination resources can be identical and the source and destination regions can overlap.

This Direct3D 11.1 feature consists of the following API.

-   [**ID3D11DeviceContext1::CopySubresourceRegion1**](./nf-d3d11_1-id3d11devicecontext1-copysubresourceregion1-2af7b964e3.md)
-   [**ID3D11DeviceContext1::UpdateSubresource1**](./nf-d3d11_1-id3d11devicecontext1-updatesubresource1-f9209fb99d.md)

## Discard resources and resource views

Direct3D 11.1 lets you discard resources and views of resources from the device context. This new functionality informs the GPU that existing content in resources or resource views are no longer needed.

This Direct3D 11.1 feature consists of the following API.

-   [**ID3D11DeviceContext1::DiscardResource**](./nf-d3d11_1-id3d11devicecontext1-discardresource-a2b50b72d2.md)
-   [**ID3D11DeviceContext1::DiscardView**](./nf-d3d11_1-id3d11devicecontext1-discardview-87a660dcab.md)
-   [**ID3D11DeviceContext1::DiscardView1**](./nf-d3d11_1-id3d11devicecontext1-discardview1-94cf75f829.md)

## Support a larger number of UAVs

Direct3D 11.1 lets you use a larger number of UAVs when you bind resources to the [output-merger stage](./d3d10-graphics-programming-guide-output-merger-stage-59e5094f74.md) and when you set an array of views for an unordered resource.

Direct3D 11.1 updates the following methods for this feature.

-   [**ID3D11DeviceContext::OMSetRenderTargetsAndUnorderedAccessViews**](./nf-d3d11-id3d11devicecontext-omsetrendertargetsandunorderedaccessviews-78c4cd3ee4.md)
-   [**ID3D11DeviceContext::CSSetUnorderedAccessViews**](./nf-d3d11-id3d11devicecontext-cssetunorderedaccessviews-c068b246d8.md)

## Bind a subrange of a constant buffer to a shader

Direct3D 11.1 lets you bind a subrange of a constant buffer for a shader to access. You can supply a larger constant buffer and specify the subrange that the shader can use.

This Direct3D 11.1 feature consists of the following API.

-   [**ID3D11DeviceContext1::CSSetConstantBuffers1**](./nf-d3d11_1-id3d11devicecontext1-cssetconstantbuffers1-3dc5274310.md)
-   [**ID3D11DeviceContext1::DSSetConstantBuffers1**](./nf-d3d11_1-id3d11devicecontext1-dssetconstantbuffers1-21a85a5475.md)
-   [**ID3D11DeviceContext1::GSSetConstantBuffers1**](./nf-d3d11_1-id3d11devicecontext1-gssetconstantbuffers1-c58003b3fe.md)
-   [**ID3D11DeviceContext1::HSSetConstantBuffers1**](./nf-d3d11_1-id3d11devicecontext1-hssetconstantbuffers1-96d2bf2bd0.md)
-   [**ID3D11DeviceContext1::PSSetConstantBuffers1**](./nf-d3d11_1-id3d11devicecontext1-pssetconstantbuffers1-08130bc0fe.md)
-   [**ID3D11DeviceContext1::VSSetConstantBuffers1**](./nf-d3d11_1-id3d11devicecontext1-vssetconstantbuffers1-dc64a3d2fa.md)

## Retrieve the subrange of a constant buffer that is bound to a shader

Direct3D 11.1 lets you retrieve the subrange of a constant buffer that is bound to a shader.

This Direct3D 11.1 feature consists of the following API.

-   [**ID3D11DeviceContext1::CSGetConstantBuffers1**](./nf-d3d11_1-id3d11devicecontext1-csgetconstantbuffers1-baa36cb05c.md)
-   [**ID3D11DeviceContext1::DSGetConstantBuffers1**](./nf-d3d11_1-id3d11devicecontext1-dsgetconstantbuffers1-de0424e980.md)
-   [**ID3D11DeviceContext1::GSGetConstantBuffers1**](./nf-d3d11_1-id3d11devicecontext1-gsgetconstantbuffers1-a1c6f81cc6.md)
-   [**ID3D11DeviceContext1::HSGetConstantBuffers1**](./nf-d3d11_1-id3d11devicecontext1-hsgetconstantbuffers1-bc2b2ac7a6.md)
-   [**ID3D11DeviceContext1::PSGetConstantBuffers1**](./nf-d3d11_1-id3d11devicecontext1-psgetconstantbuffers1-11b4619598.md)
-   [**ID3D11DeviceContext1::VSGetConstantBuffers1**](./nf-d3d11_1-id3d11devicecontext1-vsgetconstantbuffers1-3bfb985694.md)

## Clear all or part of a resource view

Direct3D 11.1 lets you clear a resource view (RTV, UAV, or any video view of a Texture2D surface). You apply the same color value to all parts of the view.

This Direct3D 11.1 feature consists of the following API.

-   [**ID3D11DeviceContext1::ClearView**](./nf-d3d11_1-id3d11devicecontext1-clearview-ed02ef0b42.md)

## Map SRVs of dynamic buffers with NO\_OVERWRITE

Direct3D 11.1 lets you map shader resource views (SRV) of dynamic buffers with D3D11\_MAP\_WRITE\_NO\_OVERWRITE. The Direct3D 11 and earlier runtimes limited mapping to vertex or index buffers.

Direct3D 11.1 updates the [**ID3D11DeviceContext::Map**](./nf-d3d11-id3d11devicecontext-map-d6df2a4196.md) method for this feature.

## Use UAVs at every pipeline stage

Direct3D 11.1 lets you use the following shader model 5.0 instructions at all shader stages that were previously used in just pixel shaders and compute shaders.

-   [dcl\_uav\_typed](/windows/desktop/direct3dhlsl/dcl-uav-typed--sm5---asm-)
-   [dcl\_uav\_raw](/windows/desktop/direct3dhlsl/dcl-uav-raw--sm5---asm-)
-   [dcl\_uav\_structured](/windows/desktop/direct3dhlsl/dcl-uav-structured--sm5---asm-)
-   [ld\_raw](/windows/desktop/direct3dhlsl/ld-raw--sm5---asm-)
-   [ld\_structured](/windows/desktop/direct3dhlsl/ld-structured--sm5---asm-)
-   [ld\_uav\_typed](/windows/desktop/direct3dhlsl/ld-uav-typed--sm5---asm-)
-   [store\_raw](/windows/desktop/direct3dhlsl/store-raw--sm5---asm-)
-   [store\_structured](/windows/desktop/direct3dhlsl/store-structured--sm5---asm-)
-   [store\_uav\_typed](/windows/desktop/direct3dhlsl/store-uav-typed--sm5---asm-)
-   [sync\_uglobal](/windows/desktop/direct3dhlsl/sync--sm5---asm-)
-   All atomics and immediate atomics (for example, [atomic\_and](/windows/desktop/direct3dhlsl/atomic-and--sm5---asm-) and [imm\_atomic\_and](/windows/desktop/direct3dhlsl/imm-atomic-and--sm5---asm-))

Direct3D 11.1 updates the following methods for this feature.

-   [**ID3D11DeviceContext::CreateDomainShader**](./nf-d3d11-id3d11device-createdomainshader-c5636e5eef.md)
-   [**ID3D11DeviceContext::CreateGeometryShader**](./nf-d3d11-id3d11device-creategeometryshader-df6444f16a.md)
-   [**ID3D11DeviceContext::CreateGeometryShaderWithStreamOutput**](./nf-d3d11-id3d11device-creategeometryshaderwithstreamoutput-bcc2201b7c.md)
-   [**ID3D11DeviceContext::CreateHullShader**](./nf-d3d11-id3d11device-createhullshader-e17ee06adf.md)
-   [**ID3D11DeviceContext::CreateVertexShader**](./nf-d3d11-id3d11device-createvertexshader-41829a40b4.md)

These instructions existed in Direct3D 11.0 in ps\_5\_0 and cs\_5\_0. Because Direct3D 11.1 makes UAVs available at all shader stages, these instructions are available at all shader stages.

If you pass compiled shaders (VS/HS/DS/HS) that use any of these instructions to a create-shader function, like [**CreateVertexShader**](./nf-d3d11-id3d11device-createvertexshader-41829a40b4.md), on devices that don’t support UAVs at every stage (including existing drivers that are not implemented with this feature), the create-shader function fails. The create-shader function also fails if the shader tries to use a UAV slot beyond the set of UAV slots that the hardware supports.

The UAVs that are referenced by these instructions are shared across all pipeline stages. For example, a UAV that is bound at slot 0 at the [output-merger stage](./d3d10-graphics-programming-guide-output-merger-stage-59e5094f74.md) is available at slot 0 to VS/HS/DS/GS/PS.

UAV accesses that you issue from within or across shader stages that execute within a given Draw\*() or that you issue from the compute shader within a Dispatch\*() aren't guaranteed to finish in the order in which you issued them. But all UAV accesses finish at the end of the Draw\*() or Dispatch\*().

## Extended support for WARP devices

Direct3D 11.1 extends support for [WARP](./overviews-direct3d-11-devices-create-warp-1c4142d50e.md) devices, which you create by passing [**D3D\_DRIVER\_TYPE\_WARP**](./ne-d3dcommon-d3d_driver_type-24df852fcc.md) in the *DriverType* parameter of [**D3D11CreateDevice**](./nf-d3d11-d3d11createdevice-fbcd3f07e1.md).

Starting with Direct3D 11.1 WARP devices support:

-   All Direct3D [feature levels](./overviews-direct3d-11-devices-downlevel-intro-f595280e88.md) from 9.1 through to 11.1
-   [Compute shaders](./direct3d-11-advanced-stages-compute-shader-5ea3c0666f.md) and [tessellation](./direct3d-11-advanced-stages-tessellation-1063a02933.md)
-   Shared surfaces. That is, you can fully share surfaces between WARP devices, as well as between WARP devices in different processes.

WARP devices don't support these optional features:

-   [doubles](./ns-d3d11-d3d11_feature_data_doubles-9388da963d.md)
-   [video encode or decode](./ne-d3d11-d3d11_create_device_flag-5572a9b222.md)
-   [minimum precision shader support](./ns-d3d11-d3d11_feature_data_shader_min_precision_support-d544fc371c.md)

When you run a virtual machine (VM), Hyper-V, with your graphics processing unit (GPU) disabled, or without a display driver, you get a WARP device whose friendly name is "Microsoft Basic Display Adapter." This WARP device can run the full Windows experience, which includes DWM, Internet Explorer, and Windows Store apps. This WARP device also supports running legacy apps that use [DirectDraw](/windows/desktop/directdraw/directdraw) or running apps that use Direct3D 3 through Direct3D 11.1.

## Use Direct3D in Session 0 processes

Starting with Windows 8 and Windows Server 2012, you can use most of the Direct3D APIs in Session 0 processes.

> [!Note]  
> These output, window, swap chain, and presentation-related APIs are not available in Session 0 processes because they don't apply to the Session 0 environment:
>
> -   [**IDXGIFactory::CreateSwapChain**](/windows/desktop/api/dxgi/nf-dxgi-idxgifactory-createswapchain)
> -   [**IDXGIFactory::GetWindowAssociation**](/windows/desktop/api/dxgi/nf-dxgi-idxgifactory-getwindowassociation)
> -   [**IDXGIFactory::MakeWindowAssociation**](/windows/desktop/api/dxgi/nf-dxgi-idxgifactory-makewindowassociation)
> -   [**IDXGIAdapter::EnumOutputs**](/windows/desktop/api/dxgi/nf-dxgi-idxgiadapter-enumoutputs)
> -   [**ID3D11Debug::SetFeatureMask**](./nf-d3d11sdklayers-id3d11debug-setfeaturemask-f6b469fa48.md)
> -   [**ID3D11Debug::SetPresentPerRenderOpDelay**](./nf-d3d11sdklayers-id3d11debug-setpresentperrenderopdelay-696ff095e5.md)
> -   [**ID3D11Debug::SetSwapChain**](./nf-d3d11sdklayers-id3d11debug-setswapchain-0261276d64.md)
> -   [**ID3D10Debug::SetFeatureMask**](/windows/desktop/api/d3d10sdklayers/nf-d3d10sdklayers-id3d10debug-setfeaturemask)
> -   [**ID3D10Debug::SetPresentPerRenderOpDelay**](/windows/desktop/api/d3d10sdklayers/nf-d3d10sdklayers-id3d10debug-setpresentperrenderopdelay)
> -   [**ID3D10Debug::SetSwapChain**](/windows/desktop/api/d3d10sdklayers/nf-d3d10sdklayers-id3d10debug-setswapchain)
> -   [**D3D10CreateDeviceAndSwapChain**](/windows/desktop/api/d3d10misc/nf-d3d10misc-d3d10createdeviceandswapchain)
> -   [**D3D10CreateDeviceAndSwapChain1**](/windows/desktop/api/d3d10_1/nf-d3d10_1-d3d10createdeviceandswapchain1)
> -   [**D3D11CreateDeviceAndSwapChain**](./nf-d3d11-d3d11createdeviceandswapchain-5744e33d11.md)
>
> If you call one of the preceding APIs in a Session 0 process, it returns [**DXGI\_ERROR\_NOT\_CURRENTLY\_AVAILABLE**](/windows/desktop/direct3ddxgi/dxgi-error).

 

## Support for shadow buffer on feature level 9

Use a subset of Direct3D 10\_0+ shadow buffer features to implement shadow effects on [feature level](./overviews-direct3d-11-devices-downlevel-intro-f595280e88.md) 9\_x. For info about what you need to do to implement shadow effects on feature level 9\_x, see [Implementing shadow buffers for Direct3D feature level 9](/previous-versions/windows/apps/jj262110(v=win.10)).

## Related topics

<dl> <dt>

[What's new in Direct3D 11](./dx-graphics-overviews-introduction-99897347f0.md)
</dt> </dl>