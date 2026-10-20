Source: [https://learn.microsoft.com/en-us/windows/win32/api/D3D11/nf-d3d11-id3d11devicecontext-iasetinputlayout](<https://learn.microsoft.com/en-us/windows/win32/api/D3D11/nf-d3d11-id3d11devicecontext-iasetinputlayout>)

# ID3D11DeviceContext::IASetInputLayout


## -description

Bind an input-layout object to the input-assembler stage.

## -parameters

### -param pInputLayout [in, optional]

Type: <b><a href="/windows/desktop/api/d3d11/nn-d3d11-id3d11inputlayout">ID3D11InputLayout</a>*</b>

A pointer to the input-layout object (see <a href="/windows/desktop/api/d3d11/nn-d3d11-id3d11inputlayout">ID3D11InputLayout</a>), which describes the input buffers that will be read by the IA stage.

## -remarks

Input-layout objects describe how vertex buffer data is streamed into the IA pipeline stage. To create an input-layout object, call <a href="/windows/desktop/api/d3d11/nf-d3d11-id3d11device-createinputlayout">ID3D11Device::CreateInputLayout</a>.

The method will hold a reference to the interfaces passed in.
      This differs from the device state behavior in Direct3D 10.

## -see-also

<a href="/windows/desktop/api/d3d11/nn-d3d11-id3d11devicecontext">ID3D11DeviceContext</a>