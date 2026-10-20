Source: [https://learn.microsoft.com/en-us/windows/win32/api/D3D11Shader/nf-d3d11shader-id3d11shaderreflectionvariable-getdesc](<https://learn.microsoft.com/en-us/windows/win32/api/D3D11Shader/nf-d3d11shader-id3d11shaderreflectionvariable-getdesc>)

# ID3D11ShaderReflectionVariable::GetDesc


## -description

Get a shader-variable description.

## -parameters

### -param pDesc [out]

Type: <b><a href="/windows/desktop/api/d3d11shader/ns-d3d11shader-d3d11_shader_variable_desc">D3D11_SHADER_VARIABLE_DESC</a>*</b>

A pointer to a shader-variable description (see <a href="/windows/desktop/api/d3d11shader/ns-d3d11shader-d3d11_shader_variable_desc">D3D11_SHADER_VARIABLE_DESC</a>).

## -returns

Type: <b><a href="/windows/win32/com/structure-of-com-error-codes">HRESULT</a></b>

Returns one of the following <a href="/windows/desktop/direct3d11/d3d11-graphics-reference-returnvalues">Direct3D 11 Return Codes</a>.

## -remarks

This method can be used to determine if the <a href="/windows/desktop/api/d3d11shader/nn-d3d11shader-id3d11shaderreflectionvariable">ID3D11ShaderReflectionVariable Interface</a> is valid, the method returns <b>E_FAIL</b> when the variable is not valid.

This method's interface is hosted in the out-of-box DLL D3DCompiler_xx.dll.

## -see-also

<a href="/windows/desktop/api/d3d11shader/nn-d3d11shader-id3d11shaderreflectionvariable">ID3D11ShaderReflectionVariable Interface</a>