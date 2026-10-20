Source: [https://learn.microsoft.com/en-us/windows/win32/api/D3D11/nf-d3d11-id3d11devicecontext-dsgetshader](<https://learn.microsoft.com/en-us/windows/win32/api/D3D11/nf-d3d11-id3d11devicecontext-dsgetshader>)

# ID3D11DeviceContext::DSGetShader


## -description

Get the domain shader currently set on the device.

## -parameters

### -param ppDomainShader [out]

Type: <b><a href="/windows/desktop/api/d3d11/nn-d3d11-id3d11domainshader">ID3D11DomainShader</a>**</b>

Address of a pointer to a domain shader (see <a href="/windows/desktop/api/d3d11/nn-d3d11-id3d11domainshader">ID3D11DomainShader</a>) to be returned by the method.

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