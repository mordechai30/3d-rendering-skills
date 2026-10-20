Source: [https://learn.microsoft.com/en-us/windows/win32/api/D3D11Shader/nf-d3d11shader-id3d11shaderreflection-getpatchconstantparameterdesc](<https://learn.microsoft.com/en-us/windows/win32/api/D3D11Shader/nf-d3d11shader-id3d11shaderreflection-getpatchconstantparameterdesc>)

# ID3D11ShaderReflection::GetPatchConstantParameterDesc


## -description

Get a patch-constant parameter description for a shader.

## -parameters

### -param ParameterIndex [in]

Type: <b><a href="/windows/desktop/WinProg/windows-data-types">UINT</a></b>

A zero-based parameter index.

### -param pDesc [out]

Type: <b><a href="/windows/win32/api/d3d11shader/ns-d3d11shader-d3d11_signature_parameter_desc">D3D11_SIGNATURE_PARAMETER_DESC</a>*</b>

A pointer to a shader-input-signature description. See <a href="/windows/win32/api/d3d11shader/ns-d3d11shader-d3d11_signature_parameter_desc">D3D11_SIGNATURE_PARAMETER_DESC</a>.

## -returns

Type: <b><a href="/windows/win32/com/structure-of-com-error-codes">HRESULT</a></b>

Returns one of the following <a href="/windows/desktop/direct3d11/d3d11-graphics-reference-returnvalues">Direct3D 11 Return Codes</a>.

## -remarks

This method's interface is hosted in the out-of-box DLL D3DCompiler_xx.dll.

## -see-also

<a href="/windows/desktop/api/d3d11shader/nn-d3d11shader-id3d11shaderreflection">ID3D11ShaderReflection Interface</a>