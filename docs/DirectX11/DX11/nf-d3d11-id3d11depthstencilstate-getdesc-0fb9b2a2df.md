Source: [https://learn.microsoft.com/en-us/windows/win32/api/D3D11/nf-d3d11-id3d11depthstencilstate-getdesc](<https://learn.microsoft.com/en-us/windows/win32/api/D3D11/nf-d3d11-id3d11depthstencilstate-getdesc>)

# ID3D11DepthStencilState::GetDesc


## -description

Gets the description for depth-stencil state that you used to create the depth-stencil-state object.

## -parameters

### -param pDesc [out]

Type: <b><a href="/windows/desktop/api/d3d11/ns-d3d11-d3d11_depth_stencil_desc">D3D11_DEPTH_STENCIL_DESC</a>*</b>

A pointer to a <a href="/windows/desktop/api/d3d11/ns-d3d11-d3d11_depth_stencil_desc">D3D11_DEPTH_STENCIL_DESC</a> structure that receives a description of the depth-stencil state.

## -remarks

You use the description for depth-stencil state in a call to the <a href="/windows/desktop/api/d3d11/nf-d3d11-id3d11device-createdepthstencilstate">ID3D11Device::CreateDepthStencilState</a> method to create the depth-stencil-state object.

## -see-also

<a href="/windows/desktop/api/d3d11/nn-d3d11-id3d11depthstencilstate">ID3D11DepthStencilState</a>