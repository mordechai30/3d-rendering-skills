Source: [https://learn.microsoft.com/en-us/windows/win32/api/D3D11Shader/nf-d3d11shader-id3d11shaderreflection-getresourcebindingdesc](<https://learn.microsoft.com/en-us/windows/win32/api/D3D11Shader/nf-d3d11shader-id3d11shaderreflection-getresourcebindingdesc>)

# ID3D11ShaderReflection::GetResourceBindingDesc


## -description

Get a description of how a resource is bound to a shader.

## -parameters

### -param ResourceIndex [in]

Type: <b><a href="/windows/desktop/WinProg/windows-data-types">UINT</a></b>

A zero-based resource index.

### -param pDesc [out]

Type: <b><a href="/windows/win32/api/d3d11shader/ns-d3d11shader-d3d11_shader_input_bind_desc">D3D11_SHADER_INPUT_BIND_DESC</a>*</b>

A pointer to an input-binding description. See <a href="/windows/win32/api/d3d11shader/ns-d3d11shader-d3d11_shader_input_bind_desc">D3D11_SHADER_INPUT_BIND_DESC</a>.

## -returns

Type: <b><a href="/windows/win32/com/structure-of-com-error-codes">HRESULT</a></b>

Returns one of the following <a href="/windows/desktop/direct3d11/d3d11-graphics-reference-returnvalues">Direct3D 11 Return Codes</a>.

## -remarks

A shader consists of executable code (the compiled HLSL functions) and a set of resources that supply the shader with input data. <b>GetResourceBindingDesc</b> gets information about how one resource in the set is bound as an input to the shader. The  <i>ResourceIndex</i> parameter specifies the index for the resource.

This method's interface is hosted in the out-of-box DLL D3DCompiler_xx.dll.

## -see-also

<a href="/windows/desktop/api/d3d11shader/nn-d3d11shader-id3d11shaderreflection">ID3D11ShaderReflection Interface</a>