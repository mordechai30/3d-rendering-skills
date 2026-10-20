Source: [https://learn.microsoft.com/en-us/windows/win32/api/D3D11_1/nf-d3d11_1-id3d11rasterizerstate1-getdesc1](<https://learn.microsoft.com/en-us/windows/win32/api/D3D11_1/nf-d3d11_1-id3d11rasterizerstate1-getdesc1>)

# ID3D11RasterizerState1::GetDesc1


## -description

Gets the description for rasterizer state that you used to create the rasterizer-state object.

## -parameters

### -param pDesc [out]

A pointer to a <a href="/windows/desktop/api/d3d11_1/ns-d3d11_1-cd3d11_rasterizer_desc1">D3D11_RASTERIZER_DESC1</a> structure that receives a description of the rasterizer state. This rasterizer state can specify forced sample count.

## -remarks

You use the description for rasterizer state in a call to the <a href="/windows/desktop/api/d3d11_1/nf-d3d11_1-id3d11device1-createrasterizerstate1">ID3D11Device1::CreateRasterizerState1</a> method to create the rasterizer-state object.

## -see-also

<a href="/windows/desktop/api/d3d11_1/nn-d3d11_1-id3d11rasterizerstate1">ID3D11RasterizerState1</a>