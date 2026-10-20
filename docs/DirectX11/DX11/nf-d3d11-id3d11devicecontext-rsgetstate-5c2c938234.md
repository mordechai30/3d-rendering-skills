Source: [https://learn.microsoft.com/en-us/windows/win32/api/D3D11/nf-d3d11-id3d11devicecontext-rsgetstate](<https://learn.microsoft.com/en-us/windows/win32/api/D3D11/nf-d3d11-id3d11devicecontext-rsgetstate>)

# ID3D11DeviceContext::RSGetState


## -description

Get the <a href="/windows/desktop/api/d3d11/ns-d3d11-d3d11_rasterizer_desc">rasterizer state</a> from the rasterizer stage of the pipeline.

## -parameters

### -param ppRasterizerState [out]

Type: <b><a href="/windows/desktop/api/d3d11/nn-d3d11-id3d11rasterizerstate">ID3D11RasterizerState</a>**</b>

Address of a pointer to a rasterizer-state interface (see <a href="/windows/desktop/api/d3d11/nn-d3d11-id3d11rasterizerstate">ID3D11RasterizerState</a>) to fill with information from the device.

## -remarks

Any returned interfaces will have their reference count incremented by one. Applications should call IUnknown::Release on the returned interfaces when they are no longer needed to avoid memory leaks.

## -see-also

<a href="/windows/desktop/api/d3d11/nn-d3d11-id3d11devicecontext">ID3D11DeviceContext</a>