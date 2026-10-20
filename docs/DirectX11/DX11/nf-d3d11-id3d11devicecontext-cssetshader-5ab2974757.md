Source: [https://learn.microsoft.com/en-us/windows/win32/api/D3D11/nf-d3d11-id3d11devicecontext-cssetshader](<https://learn.microsoft.com/en-us/windows/win32/api/D3D11/nf-d3d11-id3d11devicecontext-cssetshader>)

# ID3D11DeviceContext::CSSetShader


## -description

Set a compute shader to the device.

## -parameters

### -param pComputeShader [in, optional]

Type: <b><a href="/windows/desktop/api/d3d11/nn-d3d11-id3d11computeshader">ID3D11ComputeShader</a>*</b>

Pointer to a compute shader (see <a href="/windows/desktop/api/d3d11/nn-d3d11-id3d11computeshader">ID3D11ComputeShader</a>). Passing in <b>NULL</b> disables the shader for this pipeline stage.

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

## -see-also

<a href="/windows/desktop/api/d3d11/nn-d3d11-id3d11devicecontext">ID3D11DeviceContext</a>