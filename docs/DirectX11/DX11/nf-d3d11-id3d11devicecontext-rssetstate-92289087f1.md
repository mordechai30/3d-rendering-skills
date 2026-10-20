Source: [https://learn.microsoft.com/en-us/windows/win32/api/D3D11/nf-d3d11-id3d11devicecontext-rssetstate](<https://learn.microsoft.com/en-us/windows/win32/api/D3D11/nf-d3d11-id3d11devicecontext-rssetstate>)

# ID3D11DeviceContext::RSSetState


## -description

Set the <a href="/windows/desktop/api/d3d11/ns-d3d11-d3d11_rasterizer_desc">rasterizer state</a> for the rasterizer stage of the pipeline.

## -parameters

### -param pRasterizerState [in, optional]

Type: <b><a href="/windows/desktop/api/d3d11/nn-d3d11-id3d11rasterizerstate">ID3D11RasterizerState</a>*</b>

Pointer to a rasterizer-state interface (see <a href="/windows/desktop/api/d3d11/nn-d3d11-id3d11rasterizerstate">ID3D11RasterizerState</a>) to bind to the pipeline.

## -remarks

To create a rasterizer state interface, call <a href="/windows/desktop/api/d3d11/nf-d3d11-id3d11device-createrasterizerstate">ID3D11Device::CreateRasterizerState</a>.

The method will hold a reference to the interfaces passed in.
      This differs from the device state behavior in Direct3D 10.

## -see-also

<a href="/windows/desktop/api/d3d11/nn-d3d11-id3d11devicecontext">ID3D11DeviceContext</a>