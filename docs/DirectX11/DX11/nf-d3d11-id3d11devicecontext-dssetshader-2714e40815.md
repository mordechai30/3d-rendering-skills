Source: [https://learn.microsoft.com/en-us/windows/win32/api/D3D11/nf-d3d11-id3d11devicecontext-dssetshader](<https://learn.microsoft.com/en-us/windows/win32/api/D3D11/nf-d3d11-id3d11devicecontext-dssetshader>)

# ID3D11DeviceContext::DSSetShader


## -description

Set a domain shader to the device.

## -parameters

### -param pDomainShader [in, optional]

Type: <b><a href="/windows/desktop/api/d3d11/nn-d3d11-id3d11domainshader">ID3D11DomainShader</a>*</b>

Pointer to a domain shader (see <a href="/windows/desktop/api/d3d11/nn-d3d11-id3d11domainshader">ID3D11DomainShader</a>). Passing in <b>NULL</b> disables the shader for this pipeline stage.

### -param ppClassInstances [in, optional]

Type: <b><a href="/windows/desktop/api/d3d11/nn-d3d11-id3d11classinstance">ID3D11ClassInstance</a>*</b>

A pointer to an array of class-instance interfaces (see <a href="/windows/desktop/api/d3d11/nn-d3d11-id3d11classinstance">ID3D11ClassInstance</a>). Each interface used by a shader must have a corresponding class instance or the shader will get disabled. Set ppClassInstances to <b>NULL</b> if the shader does not use any interfaces.

### -param NumClassInstances

Type: <b><a href="/windows/desktop/WinProg/windows-data-types">UINT</a></b>

The number of class-instance interfaces in the array.

## -remarks

The method will hold a reference to the interfaces passed in.
          This differs from the device state behavior in Direct3D 10.
        

The maximum number of instances a shader can have is 256.

<b>Windows Phone 8:
        </b> This API is supported.

## -see-also

<a href="/windows/desktop/api/d3d11/nn-d3d11-id3d11devicecontext">ID3D11DeviceContext</a>