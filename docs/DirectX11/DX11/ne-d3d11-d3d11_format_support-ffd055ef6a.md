Source: [https://learn.microsoft.com/en-us/windows/win32/api/D3D11/ne-d3d11-d3d11_format_support](<https://learn.microsoft.com/en-us/windows/win32/api/D3D11/ne-d3d11-d3d11_format_support>)

# D3D11_FORMAT_SUPPORT enumeration


## -description

Which resources are supported for a given format and given device (see <a href="/windows/desktop/api/d3d11/nf-d3d11-id3d11device-checkformatsupport">ID3D11Device::CheckFormatSupport</a> 
    and <a href="/windows/desktop/api/d3d11/nf-d3d11-id3d11device-checkfeaturesupport">ID3D11Device::CheckFeatureSupport</a>).

## -enum-fields

### -field D3D11_FORMAT_SUPPORT_BUFFER:0x1

Buffer resources supported.

### -field D3D11_FORMAT_SUPPORT_IA_VERTEX_BUFFER:0x2

Vertex buffers supported.

### -field D3D11_FORMAT_SUPPORT_IA_INDEX_BUFFER:0x4

Index buffers supported.

### -field D3D11_FORMAT_SUPPORT_SO_BUFFER:0x8

Streaming output buffers supported.

### -field D3D11_FORMAT_SUPPORT_TEXTURE1D:0x10

1D texture resources supported.

### -field D3D11_FORMAT_SUPPORT_TEXTURE2D:0x20

2D texture resources supported.

### -field D3D11_FORMAT_SUPPORT_TEXTURE3D:0x40

3D texture resources supported.

### -field D3D11_FORMAT_SUPPORT_TEXTURECUBE:0x80

Cube texture resources supported.

### -field D3D11_FORMAT_SUPPORT_SHADER_LOAD:0x100

The HLSL <a href="/windows/desktop/direct3dhlsl/dx-graphics-hlsl-to-load">Load</a> function for texture objects is supported.

### -field D3D11_FORMAT_SUPPORT_SHADER_SAMPLE:0x200

The HLSL <a href="/windows/desktop/direct3dhlsl/dx-graphics-hlsl-to-sample">Sample</a> function for texture objects is supported.

<div class="alert"><b>Note</b>  If the device supports the format as a resource (1D, 2D, 3D, or cube map) but doesn't support this option, the resource can still use the <a href="/windows/desktop/direct3dhlsl/dx-graphics-hlsl-to-sample">Sample</a> method but must use only the point filtering sampler state to perform the sample.</div>
<div> </div>

### -field D3D11_FORMAT_SUPPORT_SHADER_SAMPLE_COMPARISON:0x400

The HLSL <a href="/windows/desktop/direct3dhlsl/dx-graphics-hlsl-to-samplecmp">SampleCmp</a> and <a href="/windows/desktop/direct3dhlsl/dx-graphics-hlsl-to-samplecmplevelzero">SampleCmpLevelZero</a> functions for texture objects are supported.

<div class="alert"><b>Note</b>  Windows 8 and later might provide limited support for these functions on Direct3D <a href="/windows/desktop/direct3d11/overviews-direct3d-11-devices-downlevel-intro">feature levels</a> 9_1, 9_2, and 9_3. For more info, see <a href="/previous-versions/windows/apps/jj262110(v=win.10)">Implementing shadow buffers for Direct3D feature level 9</a>.
</div>
<div> </div>

### -field D3D11_FORMAT_SUPPORT_SHADER_SAMPLE_MONO_TEXT:0x800

Reserved.

### -field D3D11_FORMAT_SUPPORT_MIP:0x1000

Mipmaps are supported.

### -field D3D11_FORMAT_SUPPORT_MIP_AUTOGEN:0x2000

Automatic generation of mipmaps is supported.

### -field D3D11_FORMAT_SUPPORT_RENDER_TARGET:0x4000

Render targets are supported.

### -field D3D11_FORMAT_SUPPORT_BLENDABLE:0x8000

Blend operations supported.

### -field D3D11_FORMAT_SUPPORT_DEPTH_STENCIL:0x10000

Depth stencils supported.

### -field D3D11_FORMAT_SUPPORT_CPU_LOCKABLE:0x20000

CPU locking supported.

### -field D3D11_FORMAT_SUPPORT_MULTISAMPLE_RESOLVE:0x40000

Multisample antialiasing (MSAA) resolve operations are supported. For more info, see <a href="/windows/desktop/api/d3d11/nf-d3d11-id3d11devicecontext-resolvesubresource">ID3D11DeviceContex::ResolveSubresource</a>.

### -field D3D11_FORMAT_SUPPORT_DISPLAY:0x80000

Format can be displayed on screen.

### -field D3D11_FORMAT_SUPPORT_CAST_WITHIN_BIT_LAYOUT:0x100000

Format cannot be cast to another format.

### -field D3D11_FORMAT_SUPPORT_MULTISAMPLE_RENDERTARGET:0x200000

Format can be used as a multisampled rendertarget.

### -field D3D11_FORMAT_SUPPORT_MULTISAMPLE_LOAD:0x400000

Format can be used as a multisampled texture and read into a shader with the HLSL load function.

### -field D3D11_FORMAT_SUPPORT_SHADER_GATHER:0x800000

Format can be used with the HLSL gather function. This value is available in DirectX 10.1 or higher.

### -field D3D11_FORMAT_SUPPORT_BACK_BUFFER_CAST:0x1000000

Format supports casting when the resource is a back buffer.

### -field D3D11_FORMAT_SUPPORT_TYPED_UNORDERED_ACCESS_VIEW:0x2000000

Format can be used for an unordered access view.

### -field D3D11_FORMAT_SUPPORT_SHADER_GATHER_COMPARISON:0x4000000

Format can be used with the HLSL gather with comparison function.

### -field D3D11_FORMAT_SUPPORT_DECODER_OUTPUT:0x8000000

Format can be used with the decoder output.

<b>Direct3D 11:  </b>This value is not supported until Direct3D 11.1.

### -field D3D11_FORMAT_SUPPORT_VIDEO_PROCESSOR_OUTPUT:0x10000000

Format can be used with the video processor output.

<b>Direct3D 11:  </b>This value is not supported until Direct3D 11.1.

### -field D3D11_FORMAT_SUPPORT_VIDEO_PROCESSOR_INPUT:0x20000000

Format can be used with the video processor input.

<b>Direct3D 11:  </b>This value is not supported until Direct3D 11.1.

### -field D3D11_FORMAT_SUPPORT_VIDEO_ENCODER:0x40000000

Format can be used with the video encoder.

<b>Direct3D 11:  </b>This value is not supported until Direct3D 11.1.

## -see-also

<a href="/windows/desktop/direct3d11/d3d11-graphics-reference-d3d11-core-enums">Core Enumerations</a>