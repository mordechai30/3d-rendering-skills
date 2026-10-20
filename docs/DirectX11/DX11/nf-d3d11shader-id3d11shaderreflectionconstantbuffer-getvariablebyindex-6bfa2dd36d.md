Source: [https://learn.microsoft.com/en-us/windows/win32/api/D3D11Shader/nf-d3d11shader-id3d11shaderreflectionconstantbuffer-getvariablebyindex](<https://learn.microsoft.com/en-us/windows/win32/api/D3D11Shader/nf-d3d11shader-id3d11shaderreflectionconstantbuffer-getvariablebyindex>)

# ID3D11ShaderReflectionConstantBuffer::GetVariableByIndex


## -description

Get a shader-reflection variable by index.

## -parameters

### -param Index [in]

Type: <b><a href="/windows/desktop/WinProg/windows-data-types">UINT</a></b>

Zero-based index.

## -returns

Type: <b><a href="/windows/desktop/api/d3d11shader/nn-d3d11shader-id3d11shaderreflectionvariable">ID3D11ShaderReflectionVariable</a>*</b>

A pointer to a shader-reflection variable interface (see <a href="/windows/desktop/api/d3d11shader/nn-d3d11shader-id3d11shaderreflectionvariable">ID3D11ShaderReflectionVariable Interface</a>).

## -remarks

This method's interface is hosted in the out-of-box DLL D3DCompiler_xx.dll.

## -see-also

<a href="/windows/desktop/api/d3d11shader/nn-d3d11shader-id3d11shaderreflectionconstantbuffer">ID3D11ShaderReflectionConstantBuffer Interface</a>