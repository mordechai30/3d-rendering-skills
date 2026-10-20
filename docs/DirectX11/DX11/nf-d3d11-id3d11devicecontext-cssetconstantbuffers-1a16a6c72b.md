Source: [https://learn.microsoft.com/en-us/windows/win32/api/D3D11/nf-d3d11-id3d11devicecontext-cssetconstantbuffers](<https://learn.microsoft.com/en-us/windows/win32/api/D3D11/nf-d3d11-id3d11devicecontext-cssetconstantbuffers>)

# ID3D11DeviceContext::CSSetConstantBuffers


## -description

Sets the constant buffers used by the compute-shader stage.

## -parameters

### -param StartSlot [in]

Type: <b><a href="/windows/desktop/WinProg/windows-data-types">UINT</a></b>

Index into the zero-based array to begin setting constant buffers to (ranges from 0 to <b>D3D11_COMMONSHADER_CONSTANT_BUFFER_API_SLOT_COUNT</b> - 1).

### -param NumBuffers [in]

Type: <b><a href="/windows/desktop/WinProg/windows-data-types">UINT</a></b>

Number of buffers to set (ranges from 0 to <b>D3D11_COMMONSHADER_CONSTANT_BUFFER_API_SLOT_COUNT</b> - <i>StartSlot</i>).

### -param ppConstantBuffers [in, optional]

Type: <b><a href="/windows/desktop/api/d3d11/nn-d3d11-id3d11buffer">ID3D11Buffer</a>*</b>

Array of constant buffers (see <a href="/windows/desktop/api/d3d11/nn-d3d11-id3d11buffer">ID3D11Buffer</a>) being given to the device.

## -remarks

The method will hold a reference to the interfaces passed in.
      This differs from the device state behavior in Direct3D 10.

The Direct3D 11.1 runtime, which is available starting with Windows 8, can bind a larger number of <a href="/windows/desktop/api/d3d11/nn-d3d11-id3d11buffer">ID3D11Buffer</a> resources to the shader than the maximum constant buffer size that is supported by shaders (4096 constants – 4\*32-bit components each).  When you bind such a large buffer, the shader can access only the first 4096 4\*32-bit component constants in the buffer, as if 4096 constants is the full size of the buffer.  

If the application wants the shader to access other parts of the buffer, it must call the <a href="/windows/desktop/api/d3d11_1/nf-d3d11_1-id3d11devicecontext1-cssetconstantbuffers1">CSSetConstantBuffers1</a> method instead.

## -see-also

<a href="/windows/desktop/api/d3d11/nn-d3d11-id3d11devicecontext">ID3D11DeviceContext</a>