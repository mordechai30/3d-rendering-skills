Source: [https://learn.microsoft.com/en-us/windows/win32/api/D3D11Shader/nf-d3d11shader-id3d11shaderreflectiontype-isoftype](<https://learn.microsoft.com/en-us/windows/win32/api/D3D11Shader/nf-d3d11shader-id3d11shaderreflectiontype-isoftype>)

# ID3D11ShaderReflectionType::IsOfType


## -description

Indicates whether a variable is of the specified type.

## -parameters

### -param pType [in]

Type: <b><a href="/windows/desktop/api/d3d11shader/nn-d3d11shader-id3d11shaderreflectiontype">ID3D11ShaderReflectionType</a>*</b>

A pointer to a <a href="/windows/desktop/api/d3d11shader/nn-d3d11shader-id3d11shaderreflectiontype">ID3D11ShaderReflectionType Interface</a>.

## -returns

Type: <b><a href="/windows/win32/com/structure-of-com-error-codes">HRESULT</a></b>

Returns S_OK if object being queried is equal to or inherits from the type in the <i>pType</i> parameter; otherwise returns S_FALSE.

## -remarks

This method's interface is hosted in the out-of-box DLL D3DCompiler_xx.dll.

## -see-also

<a href="/windows/desktop/api/d3d11shader/nn-d3d11shader-id3d11shaderreflectiontype">ID3D11ShaderReflectionType Interface</a>