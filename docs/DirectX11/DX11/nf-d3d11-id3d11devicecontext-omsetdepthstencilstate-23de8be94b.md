Source: [https://learn.microsoft.com/en-us/windows/win32/api/D3D11/nf-d3d11-id3d11devicecontext-omsetdepthstencilstate](<https://learn.microsoft.com/en-us/windows/win32/api/D3D11/nf-d3d11-id3d11devicecontext-omsetdepthstencilstate>)

# ID3D11DeviceContext::OMSetDepthStencilState


## -description

Sets the depth-stencil state of the output-merger stage.

## -parameters

### -param pDepthStencilState [in, optional]

Type: <b><a href="/windows/desktop/api/d3d11/nn-d3d11-id3d11depthstencilstate">ID3D11DepthStencilState</a>*</b>

Pointer to a depth-stencil state interface (see <a href="/windows/desktop/api/d3d11/nn-d3d11-id3d11depthstencilstate">ID3D11DepthStencilState</a>) to bind to the device. Set this to <b>NULL</b> to use the default state listed in <a href="/windows/desktop/api/d3d11/ns-d3d11-d3d11_depth_stencil_desc">D3D11_DEPTH_STENCIL_DESC</a>.

### -param StencilRef [in]

Type: <b><a href="/windows/desktop/WinProg/windows-data-types">UINT</a></b>

Reference value to perform against when doing a depth-stencil test. See remarks.

## -remarks

To create a depth-stencil state interface, call <a href="/windows/desktop/api/d3d11/nf-d3d11-id3d11device-createdepthstencilstate">ID3D11Device::CreateDepthStencilState</a>.

The method will hold a reference to the interfaces passed in.
      This differs from the device state behavior in Direct3D 10.

## -see-also

<a href="/windows/desktop/api/d3d11/nn-d3d11-id3d11devicecontext">ID3D11DeviceContext</a>