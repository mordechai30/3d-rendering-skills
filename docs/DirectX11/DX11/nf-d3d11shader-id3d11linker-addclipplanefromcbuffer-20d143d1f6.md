Source: [https://learn.microsoft.com/en-us/windows/win32/api/D3D11Shader/nf-d3d11shader-id3d11linker-addclipplanefromcbuffer](<https://learn.microsoft.com/en-us/windows/win32/api/D3D11Shader/nf-d3d11shader-id3d11linker-addclipplanefromcbuffer>)

# ID3D11Linker::AddClipPlaneFromCBuffer


## -description

Adds a <a href="/windows/desktop/direct3dhlsl/user-clip-planes-on-10level9">clip plane</a> with the plane coefficients taken from a <a href="/windows/desktop/direct3dhlsl/dx-graphics-hlsl-constants">cbuffer</a> entry for 10Level9 shaders.

## -parameters

### -param uCBufferSlot [in]

Type: <b><a href="/windows/desktop/WinProg/windows-data-types">UINT</a></b>

The <a href="/windows/desktop/direct3dhlsl/dx-graphics-hlsl-constants">cbuffer</a> slot number.

### -param uCBufferEntry [in]

Type: <b><a href="/windows/desktop/WinProg/windows-data-types">UINT</a></b>

The <a href="/windows/desktop/direct3dhlsl/dx-graphics-hlsl-constants">cbuffer</a> entry number.

## -returns

Type: <b><a href="/windows/win32/com/structure-of-com-error-codes">HRESULT</a></b>

Returns S_OK if successful; otherwise, returns one of the <a href="/windows/desktop/direct3d11/d3d11-graphics-reference-returnvalues">Direct3D 11 Return Codes</a>.

## -see-also

<a href="/windows/desktop/api/d3d11shader/nn-d3d11shader-id3d11linker">ID3D11Linker</a>