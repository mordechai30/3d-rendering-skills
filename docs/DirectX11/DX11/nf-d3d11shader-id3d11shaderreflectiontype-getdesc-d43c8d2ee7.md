Source: [https://learn.microsoft.com/en-us/windows/win32/api/D3D11Shader/nf-d3d11shader-id3d11shaderreflectiontype-getdesc](<https://learn.microsoft.com/en-us/windows/win32/api/D3D11Shader/nf-d3d11shader-id3d11shaderreflectiontype-getdesc>)

# ID3D11ShaderReflectionType::GetDesc


## -description

Get the description of a shader-reflection-variable type.

## -parameters

### -param pDesc [out]

Type: <b><a href="/windows/desktop/api/d3d11shader/ns-d3d11shader-d3d11_shader_type_desc">D3D11_SHADER_TYPE_DESC</a>*</b>

A pointer to a shader-type description (see <a href="/windows/desktop/api/d3d11shader/ns-d3d11shader-d3d11_shader_type_desc">D3D11_SHADER_TYPE_DESC</a>).

## -returns

Type: <b><a href="/windows/win32/com/structure-of-com-error-codes">HRESULT</a></b>

Returns one of the following <a href="/windows/desktop/direct3d11/d3d11-graphics-reference-returnvalues">Direct3D 11 Return Codes</a>.

## -remarks

This method's interface is hosted in the out-of-box DLL D3DCompiler_xx.dll.

## -see-also

<a href="/windows/desktop/api/d3d11shader/nn-d3d11shader-id3d11shaderreflectiontype">ID3D11ShaderReflectionType Interface</a>