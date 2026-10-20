Source: [https://learn.microsoft.com/en-us/windows/win32/api/D3D11/nf-d3d11-id3d11devicecontext-vsgetshader](<https://learn.microsoft.com/en-us/windows/win32/api/D3D11/nf-d3d11-id3d11devicecontext-vsgetshader>)

# ID3D11DeviceContext::VSGetShader


## -description

Get the vertex shader currently set on the device.

## -parameters

### -param ppVertexShader [out]

Type: <b><a href="/windows/desktop/api/d3d11/nn-d3d11-id3d11vertexshader">ID3D11VertexShader</a>**</b>

Address of a pointer to a vertex shader (see <a href="/windows/desktop/api/d3d11/nn-d3d11-id3d11vertexshader">ID3D11VertexShader</a>) to be returned by the method.

### -param ppClassInstances [out, optional]

Type: <b><a href="/windows/desktop/api/d3d11/nn-d3d11-id3d11classinstance">ID3D11ClassInstance</a>**</b>

Pointer to an array of class instance interfaces (see <a href="/windows/desktop/api/d3d11/nn-d3d11-id3d11classinstance">ID3D11ClassInstance</a>).

### -param pNumClassInstances [in, out, optional]

Type: <b><a href="/windows/desktop/WinProg/windows-data-types">UINT</a>*</b>

The number of class-instance elements in the array.

## -remarks

Any returned interfaces will have their reference count incremented by one. Applications should call IUnknown::Release on the returned interfaces when they are no longer needed to avoid memory leaks.

## -see-also

<a href="/windows/desktop/api/d3d11/nn-d3d11-id3d11devicecontext">ID3D11DeviceContext</a>