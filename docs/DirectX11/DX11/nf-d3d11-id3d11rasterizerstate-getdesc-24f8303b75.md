Source: [https://learn.microsoft.com/en-us/windows/win32/api/D3D11/nf-d3d11-id3d11rasterizerstate-getdesc](<https://learn.microsoft.com/en-us/windows/win32/api/D3D11/nf-d3d11-id3d11rasterizerstate-getdesc>)

# ID3D11RasterizerState::GetDesc


## -description

Gets the description for rasterizer state that you used to create the rasterizer-state object.

## -parameters

### -param pDesc [out]

Type: <b><a href="/windows/desktop/api/d3d11/ns-d3d11-d3d11_rasterizer_desc">D3D11_RASTERIZER_DESC</a>*</b>

A pointer to a <a href="/windows/desktop/api/d3d11/ns-d3d11-d3d11_rasterizer_desc">D3D11_RASTERIZER_DESC</a> structure that receives a description of the rasterizer state.

## -remarks

You use the description for rasterizer state in a call to the <a href="/windows/desktop/api/d3d11/nf-d3d11-id3d11device-createrasterizerstate">ID3D11Device::CreateRasterizerState</a> method to create the rasterizer-state object.

## -see-also

<a href="/windows/desktop/api/d3d11/nn-d3d11-id3d11rasterizerstate">ID3D11RasterizerState</a>