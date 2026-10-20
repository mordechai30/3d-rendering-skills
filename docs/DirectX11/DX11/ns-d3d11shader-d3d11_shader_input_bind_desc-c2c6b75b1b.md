Source: [https://learn.microsoft.com/en-us/windows/win32/api/D3D11Shader/ns-d3d11shader-d3d11_shader_input_bind_desc](<https://learn.microsoft.com/en-us/windows/win32/api/D3D11Shader/ns-d3d11shader-d3d11_shader_input_bind_desc>)

# D3D11_SHADER_INPUT_BIND_DESC structure


## -description

Describes how a shader resource is bound to a shader input.

## -struct-fields

### -field Name

Type: <b><a href="/windows/desktop/WinProg/windows-data-types">LPCSTR</a></b>

Name of the shader resource.

### -field Type

Type: <b><a href="/windows/desktop/api/d3dcommon/ne-d3dcommon-d3d_shader_input_type">D3D_SHADER_INPUT_TYPE</a></b>

A <a href="/windows/desktop/api/d3dcommon/ne-d3dcommon-d3d_shader_input_type">D3D_SHADER_INPUT_TYPE</a>-typed value that identifies the type of data in the resource.

### -field BindPoint

Type: <b><a href="/windows/desktop/WinProg/windows-data-types">UINT</a></b>

Starting bind point.

### -field BindCount

Type: <b><a href="/windows/desktop/WinProg/windows-data-types">UINT</a></b>

Number of contiguous bind points for arrays.

### -field uFlags

Type: <b><a href="/windows/desktop/WinProg/windows-data-types">UINT</a></b>

A combination of <a href="/windows/desktop/api/d3dcommon/ne-d3dcommon-d3d_shader_input_flags">D3D_SHADER_INPUT_FLAGS</a>-typed values for shader input-parameter options.

### -field ReturnType

Type: <b><a href="/windows/desktop/api/d3dcommon/ne-d3dcommon-d3d_resource_return_type">D3D_RESOURCE_RETURN_TYPE</a></b>

If the input is a texture, the <a href="/windows/desktop/api/d3dcommon/ne-d3dcommon-d3d_resource_return_type">D3D_RESOURCE_RETURN_TYPE</a>-typed value that identifies the return type.

### -field Dimension

Type: <b><a href="/windows/desktop/api/d3dcommon/ne-d3dcommon-d3d_srv_dimension">D3D_SRV_DIMENSION</a></b>

A <a href="/windows/desktop/api/d3dcommon/ne-d3dcommon-d3d_srv_dimension">D3D_SRV_DIMENSION</a>-typed value that identifies the dimensions of the bound resource.

### -field NumSamples

Type: <b><a href="/windows/desktop/WinProg/windows-data-types">UINT</a></b>

The number of samples for a multisampled texture; when a texture isn't multisampled, the value is set to -1 (0xFFFFFFFF).

## -remarks

Get a shader-input-signature description by calling <a href="/windows/desktop/api/d3d11shader/nf-d3d11shader-id3d11shaderreflection-getresourcebindingdesc">ID3D11ShaderReflection::GetResourceBindingDesc</a> or <a href="/windows/desktop/api/d3d11shader/nf-d3d11shader-id3d11shaderreflection-getresourcebindingdescbyname">ID3D11ShaderReflection::GetResourceBindingDescByName</a>.

## -see-also

<a href="/windows/desktop/direct3d11/d3d11-graphics-reference-shader-structures">Shader Structures</a>