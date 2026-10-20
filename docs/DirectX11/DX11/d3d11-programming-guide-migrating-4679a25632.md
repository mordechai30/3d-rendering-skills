Source: [https://learn.microsoft.com/en-us/windows/win32/direct3d11/d3d11-programming-guide-migrating](<https://learn.microsoft.com/en-us/windows/win32/direct3d11/d3d11-programming-guide-migrating>)

# Migrating to Direct3D 11

This section provides info for migrating to Direct3D 11 from an earlier version of Direct3D.

-   [Direct3D 9 to Direct3D 11](#direct3d-9-to-direct3d-11)
-   [Direct3D 10 to Direct3D 11](#direct3d-10-to-direct3d-11)
    -   [Enumerations and Defines](#enumerations-and-defines)
    -   [Structures](#structures)
    -   [Interfaces](#interfaces)
    -   [Other Related Technologies](#other-related-technologies)
-   [Direct3D 10.1 to Direct3D 11](#direct3d-101-to-direct3d-11)
    -   [Enumerations and Defines](#enumerations-and-defines)
    -   [Structures](#structures)
    -   [Interfaces](#interfaces)
-   [New Features for Direct3D 11](#new-features-for-direct3d-11)
-   [New Features for DirectX 11.1](#new-features-for-directx-111)
-   [New Features for DirectX 11.2](#new-features-for-directx-112)
-   [Related topics](#related-topics)

## Direct3D 9 to Direct3D 11

The Direct3D 11 API builds on the infrastructural improvements made in Direct3D 10 and 10.1. Porting from Direct3D 9 to Direct3D 11 is similar to moving from Direct3D 9 to Direct3D 10. The following are the key challenges in this effort.

-   Removal of all fixed function pipeline usage in favor of programmable shaders authored exclusively in HLSL (compiled via D3DCompiler instead of D3DX9).
-   State management based on immutable objects rather than individual state toggles.
-   Updating to comply with strict linkage requirements of vertex buffer input layouts and shader signatures.
-   Associating shader resource views with all texture resources.
-   Mapping all image content to a DXGI\_FORMAT, including the removal of all 24-bit color formats (8/8/8), and strict RGB color ordering for most scenarios.
-   Breaking up global constant state usage into several small, more efficiently updated constant buffers.

For more information about moving from Direct3D 9 to Direct3D 10, see [Direct3D 9 to Direct3D 10 Considerations](/windows/desktop/direct3d10/d3d10-graphics-programming-guide-d3d9-to-d3d10-considerations).

## Direct3D 10 to Direct3D 11

Converting programs written to use the Direct3D 10 or 10.1 API is a straight-forward process as Direct3D 11 is an extension of the existing API. With only one minor exception (noted below - monochrome text filtering), all methods and functionality in Direct3D 10/10.1 is available in Direct3D 11. The outline below describes the differences between the two APIs to aid in updating existing code. The key differences here include:

-   Rendering operations (Draw, state, etc.) are no longer part of the Device interface, but are instead part of the new DeviceContext interface along with resource Map/Unmap and device query methods.
-   Direct3D 11 includes all enhancements and changes made between Direct3D 10.0 and 10.1

### Enumerations and Defines



| Direct3D 10                            | Direct3D 11                                                                                                                                                                                                                                                                                                                                                                                                                  |
|----------------------------------------|------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| DXGI\_FORMAT                           | [**DXGI\_FORMAT**](/windows/desktop/api/dxgiformat/ne-dxgiformat-dxgi_format)Several new DXGI formats were defined.<br/>                                                                                                                                                                                                                                                                                                                                |
| D3D10\_CREATE\_DEVICE\_SWITCH\_TO\_REF | [**D3D11\_CREATE\_DEVICE\_SWITCH\_TO\_REF**](./ne-d3d11-d3d11_create_device_flag-5572a9b222.md)The switch-to-ref functionality is not supported by Direct3D 11.<br/>                                                                                                                                                                                                                                                                        |
| D3D10\_DRIVER\_TYPE                    | [**D3D\_DRIVER\_TYPE**](./ne-d3dcommon-d3d_driver_type-24df852fcc.md)Note that the enumeration identifiers in [**D3D\_DRIVER\_TYPE**](./ne-d3dcommon-d3d_driver_type-24df852fcc.md) were redefined from the identifiers in [**D3D10\_DRIVER\_TYPE**](/windows/desktop/api/d3d10misc/ne-d3d10misc-d3d10_driver_type). Therefore, you should be sure to use the enumeration identifiers instead of literal numbers.<br/> [**D3D\_DRIVER\_TYPE**](./ne-d3dcommon-d3d_driver_type-24df852fcc.md) is defined in D3Dcommon.h.<br/> |
| D3D10\_RESOURCE\_MISC\_FLAG            | [**D3D11\_RESOURCE\_MISC\_FLAG**](./ne-d3d11-d3d11_resource_misc_flag-f85f09a16f.md)Note that many of these flags were redefined, so be sure to use enumeration identifiers instead of literal numbers.<br/>                                                                                                                                                                                                                                |
| D3D10\_FILTER                          | [**D3D11\_FILTER**](./ne-d3d11-d3d11_filter-a120f82347.md)Note that text filtering D3D10\_FILTER\_TEXT\_1BIT was removed from Direct3D 11. See DirectWrite.<br/>                                                                                                                                                                                                                                                                            |
| D3D10\_COUNTER                         | [**D3D11\_COUNTER**](./ne-d3d11-d3d11_counter-f343937fca.md)Note that the vendor-neutral counters were removed for Direct3D 11 as they were rarely supported.<br/>                                                                                                                                                                                                                                                                          |
| D3D10\_x                               | D3D11\_x Many enumerations and defines are the same, have larger limits, or have additional values.<br/>                                                                                                                                                                                                                                                                                                               |



 

### Structures



| Direct3D 10                              | Direct3D 11                                                                                                                                                 |
|------------------------------------------|-------------------------------------------------------------------------------------------------------------------------------------------------------------|
| D3D10\_SO\_DECLARATION\_ENTRY            | [**D3D11\_SO\_DECLARATION\_ENTRY**](./ns-d3d11-d3d11_so_declaration_entry-06e8ae5c22.md)Adds Stream.<br/>                                                                  |
| D3D10\_BLEND\_DESC                       | [**D3D11\_BLEND\_DESC**](./ns-d3d11-d3d11_blend_desc-dbb11ca57b.md)Note this structure changed significantly from 10 to 10.1 to provide per render target blend state<br/> |
| D3D10\_BUFFER\_DESC                      | [**D3D11\_BUFFER\_DESC**](./ns-d3d11-d3d11_buffer_desc-dbbb31b85c.md)Adds a StructureByteStride for use with Compute Shader resources<br/>                                 |
| D3D10\_SHADER\_RESOURCE\_VIEW\_DESC      | [**D3D11\_SHADER\_RESOURCE\_VIEW\_DESC**](./ns-d3d11-d3d11_shader_resource_view_desc-a2ad888d5c.md)Note this structure had additional union members added for 10.1<br/>    |
| D3D10\_DEPTH\_STENCIL\_VIEW\_DESC        | [**D3D11\_DEPTH\_STENCIL\_VIEW\_DESC**](./ns-d3d11-d3d11_depth_stencil_view_desc-0538facd4a.md)Has a new Flags member.<br/>                                                |
| D3D10\_QUERY\_DATA\_PIPELINE\_STATISTICS | [**D3D11\_QUERY\_DATA\_PIPELINE\_STATISTICS**](./ns-d3d11-d3d11_query_data_pipeline_statistics-0ba5b7238b.md)Adds several new shader stage counters.<br/>                  |
| D3D10\_x                                 | D3D11\_x Many structures are identical between the two APIs.<br/>                                                                                     |



 

### Interfaces



| Direct3D 10        | Direct3D 11                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                              |
|--------------------|----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| ID3D10Device       | [**ID3D11Device**](./nn-d3d11-id3d11device-6e49ef4b9e.md) and [**ID3D11DeviceContext**](./nn-d3d11-id3d11devicecontext-abe911f651.md)<br/> The device interface was split into these two parts. For quick porting you can make use of [**ID3D11Device::GetImmediateContext**](./nf-d3d11-id3d11device-getimmediatecontext-f2c85872b1.md).<br/> "ID3D10Device::GetTextFilterSize" and "SetTextFilerSize" methods no longer exist. See DirectWrite.<br/> Create\*Shader takes an additional optional parameter for [**ID3D11ClassLinkage**](./nn-d3d11-id3d11classlinkage-1ba2aee983.md).<br/> \*SetShader and \*GetShader take additional optional parameters for [**ID3D11ClassInstance**](./nn-d3d11-id3d11classinstance-60b20918e7.md)(s).<br/> [**CreateGeometryShaderWithStreamOutput**](./nf-d3d11-id3d11device-creategeometryshaderwithstreamoutput-bcc2201b7c.md) takes an array and count for multiple output stream strides.<br/> The limit for the NumEntries parameter of [**CreateGeometryShaderWithStreamOutput**](./nf-d3d11-id3d11device-creategeometryshaderwithstreamoutput-bcc2201b7c.md) has increased to D3D11\_SO\_STREAM\_COUNT \* D3D11\_SO\_OUTPUT\_COMPONENT\_COUNT in Direct3D 11.<br/> |
| ID3D10Buffer       | [**ID3D11Buffer**](./nn-d3d11-id3d11buffer-0e4ba9908b.md)                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                     |
| ID3D10SwitchToRef  | [**ID3D11SwitchToRef**](./nn-d3d11sdklayers-id3d11switchtoref-c202d541c8.md)Switch-to-ref functionality is not supported in Direct3D 11.<br/>                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                    |
| ID3D10Texture1D    | [**ID3D11Texture1D**](./nn-d3d11-id3d11texture1d-8050524d5a.md)                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                               |
| ID3D10Texture2D    | [**ID3D11Texture2D**](./nn-d3d11-id3d11texture2d-c08b027a6d.md)                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                               |
| ID3D10Texture3D    | [**ID3D11Texture3D**](./nn-d3d11-id3d11texture3d-16e7cb8495.md)The Map and Unmap methods were moved to [**ID3D11DeviceContext**](./nn-d3d11-id3d11devicecontext-abe911f651.md), and all Map methods use [**D3D11\_MAPPED\_SUBRESOURCE**](./ns-d3d11-d3d11_mapped_subresource-5dbbf0bcb8.md) instead of a void\*\*.<br/>                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                           |
| ID3D10Asynchronous | [**ID3D11Asynchronous**](./nn-d3d11-id3d11asynchronous-8ec1287817.md)Begin, End, and GetData were moved to [**ID3D11DeviceContext**](./nn-d3d11-id3d11devicecontext-abe911f651.md).<br/>                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                     |
| ID3D10x            | ID3D11x Many interfaces are identical between the two APIs.<br/>                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                   |



 

### Other Related Technologies




| 10/10.1 Solution | 11 Solution | 
|------------------|-------------|
| HLSL Complier (D3D10Compile*, D3DX10Compile*) and shader reflection APIs | D3DCompiler (see D3DCompiler.h) **Note:** For Windows Store apps, the [D3DCompiler APIs](/windows/desktop/direct3dhlsl/dx-graphics-d3dcompiler-reference) are supported only for development, not deployment.<br> | 
| Effects 10 | [Effects 11](https://github.com/Microsoft/FX11) is available as shared source online. **Note:** This solution is not suited to Windows Store apps because it requires the [D3DCompiler APIs](/windows/desktop/direct3dhlsl/dx-graphics-d3dcompiler-reference) at runtime (deployment).<br> | 
| D3DX9/D3DX10 Math | <a href="/windows/desktop/dxmath/directxmath-portal">DirectXMath</a> | 
| D3DX10 | D3DX11 in the legacy DirectX SDK <a href="https://github.com/Microsoft/DirectXTex">DirectXTex</a>, <a href="https://github.com/Microsoft/DirectXTK">DirectXTK</a>, and <a href="https://github.com/Microsoft/DirectXMesh">DirectXMesh</a> offer alternatives to many technologies in the legacy D3DX10 and D3DX11 libraries.<br /><a href="/windows/desktop/Direct2D/direct2d-portal">Direct2D</a> and <a href="/windows/desktop/DirectWrite/direct-write-portal">DirectWrite</a> offer high-quality support for rendering styled lines and fonts.<br /> | 




 

For info about the legacy DirectX SDK, see [Where is the DirectX SDK?](/windows/desktop/directx-sdk--august-2009-).

## Direct3D 10.1 to Direct3D 11

Direct3D 10.1 is an extension of the Direct3D 10 interface, and all features of Direct3D 10.1 are available in Direct3D 11. Most of the porting from 10.1 to 11 is already addressed above moving from 10 to 11.

### Enumerations and Defines



| Direct3D 10.1          | Direct3D 11                                                                                                                                                                                                                                                                                                                                                                                                                     |
|------------------------|---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| D3D10\_FEATURE\_LEVEL1 | [**D3D\_FEATURE\_LEVEL**](./ne-d3dcommon-d3d_feature_level-fa6ac3128b.md)Identical but defined in D3DCommon.h plus the addition of D3D\_FEATURE\_LEVEL\_11\_0 for 11 class hardware along with D3D\_FEATURE\_LEVEL\_9\_1, D3D\_FEATURE\_LEVEL\_9\_2, and D3D\_FEATURE\_LEVEL\_9\_3 for 10level9<br/> (D3D10\_FEATURE\_LEVEL\_9\_1, D3D10\_FEATURE\_LEVEL\_9\_2, and D3D10\_FEATURE\_LEVEL\_9\_3 were also added for 10.1 to d3d10\_1.h)<br/> |



 

### Structures



| Direct3D 10.1                        | Direct3D 11                                                                                                                   |
|--------------------------------------|-------------------------------------------------------------------------------------------------------------------------------|
| D3D10\_BLEND\_DESC1                  | [**D3D11\_BLEND\_DESC**](./ns-d3d11-d3d11_blend_desc-dbb11ca57b.md)The 11 version is identical to 10.1.<br/>                                 |
| D3D10\_SHADER\_RESOURCE\_VIEW\_DESC1 | [**D3D11\_SHADER\_RESOURCE\_VIEW\_DESC**](./ns-d3d11-d3d11_shader_resource_view_desc-a2ad888d5c.md)The 11 version is identical to 10.1.<br/> |



 

### Interfaces



| Direct3D 10.1             | Direct3D 11                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                               |
|---------------------------|-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| ID3D10Device1             | [**ID3D11Device**](./nn-d3d11-id3d11device-6e49ef4b9e.md) and [**ID3D11DeviceContext**](./nn-d3d11-id3d11devicecontext-abe911f651.md)<br/> The device interface was split into these two parts. For quick porting you can make use of [**ID3D11Device::GetImmediateContext**](./nf-d3d11-id3d11device-getimmediatecontext-f2c85872b1.md).<br/> " ID3D10Device::GetTextFilterSize" and "SetTextFilerSize" methods no longer exist. See DirectWrite.<br/> Create\*Shader takes an additional optional parameter for [**ID3D11ClassLinkage**](./nn-d3d11-id3d11classlinkage-1ba2aee983.md).<br/> \*SetShader and \*GetShader take additional optional parameters for [**ID3D11ClassInstance**](./nn-d3d11-id3d11classinstance-60b20918e7.md)(s).<br/> [**CreateGeometryShaderWithStreamOutput**](./nf-d3d11-id3d11device-creategeometryshaderwithstreamoutput-bcc2201b7c.md) takes an array and count for multiple output stream strides.<br/> The limit for the NumEntries parameter of [**CreateGeometryShaderWithStreamOutput**](./nf-d3d11-id3d11device-creategeometryshaderwithstreamoutput-bcc2201b7c.md) has increased to D3D11\_SO\_STREAM\_COUNT \* D3D11\_SO\_OUTPUT\_COMPONENT\_COUNT in Direct3D 11.<br/> |
| ID3D10BlendState1         | [**ID3D11BlendState**](./nn-d3d11-id3d11blendstate-c89e087e23.md)                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                              |
| ID3D10ShaderResourceView1 | [**ID3D11ShaderResourceView**](./nn-d3d11-id3d11shaderresourceview-e26d3e0c03.md)                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                              |



 

## New Features for Direct3D 11

Once your code is updated to use the Direct3D 11 API, there are numerous [new features](./direct3d-11-features-a062c55bb8.md) to consider.

-   Multithreaded rendering through command lists and multiple contexts
-   Implementing advanced algorithms using Compute Shader (using 4.0, 4.1, or 5.0 shader profiles)
-   New 11 class hardware features:
    -   HLSL Shader Model 5.0
    -   Dynamic Shader Linkage
    -   Tessellation through Hull and Domain shaders
    -   New block compression formats: BC6H for HDR images, BC7 for higher-fidelity standard images
-   Utilizing [10level9 technology](./overviews-direct3d-11-devices-downlevel-366ef41a88.md) for rendering on many Shader Model 2.0 and Shader Model 3.0 devices through the DIrect3D 11 API for lower-end video hardware support on Windows Vista and Windows 7.
-   Leveraging the WARP software rendering device.

## New Features for DirectX 11.1

Windows 8 includes further DirectX graphics enhancements to consider when you implement your DirectX graphics code, which include [Direct3D 11.1](./direct3d-11-features-a062c55bb8.md), [DXGI 1.2](/windows/desktop/direct3ddxgi/dxgi-1-2-improvements), [Windows Display Driver Model (WDDM) 1.2](/windows-hardware/drivers/display/wddm-in-windows-8), [feature level](./overviews-direct3d-11-devices-downlevel-intro-f595280e88.md) 11.1 hardware, Direct2D device contexts, and other improvements.

Partial support for [Direct3D 11.1](./direct3d-11-features-a062c55bb8.md) is available on Windows 7 as well via the [Platform Update for Windows 7](/windows/desktop/direct3darticles/platform-update-for-windows-7), which is available through the [Platform Update for Windows 7](https://support.microsoft.com/kb/2670838).

## New Features for DirectX 11.2

The Windows 8.1 includes [Direct3D 11.2](./direct3d-11-2-features-468725ccb6.md), [DXGI 1.3](/windows/desktop/direct3ddxgi/dxgi-1-3-improvements), and other improvements.

## Related topics

<dl> <dt>

[Programming Guide for Direct3D 11](./dx-graphics-overviews-1c65710e07.md)
</dt> <dt>

[Effects (Direct3D 11)](./d3d11-graphics-programming-guide-effects-16146534b6.md)
</dt> </dl>