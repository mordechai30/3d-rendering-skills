Source: [https://learn.microsoft.com/en-us/windows/win32/api/D3D11_3/nf-d3d11_3-id3d11rasterizerstate2-getdesc2](<https://learn.microsoft.com/en-us/windows/win32/api/D3D11_3/nf-d3d11_3-id3d11rasterizerstate2-getdesc2>)

# ID3D11RasterizerState2::GetDesc2


## -description

Gets the description for rasterizer state that you used to create the rasterizer-state object.

## -parameters

### -param pDesc [out]

A pointer to a <a href="/windows/desktop/api/d3d11_3/ns-d3d11_3-cd3d11_rasterizer_desc2">D3D11_RASTERIZER_DESC2</a> structure that receives a description of the rasterizer state. This rasterizer state can specify forced sample count and conservative rasterization mode.

## -remarks

You use the description for rasterizer state in a call to the <a href="/windows/desktop/api/d3d11_3/nf-d3d11_3-id3d11device3-createrasterizerstate2">ID3D11Device3::CreateRasterizerState2</a> method to create the rasterizer-state object.

## -see-also

<a href="/windows/desktop/api/d3d11_3/nn-d3d11_3-id3d11rasterizerstate2">ID3D11RasterizerState2</a>