Source: [https://learn.microsoft.com/en-us/windows/win32/api/D3D11/nf-d3d11-id3d11blendstate-getdesc](<https://learn.microsoft.com/en-us/windows/win32/api/D3D11/nf-d3d11-id3d11blendstate-getdesc>)

# ID3D11BlendState::GetDesc


## -description

Gets the description for blending state that you used to create the blend-state object.

## -parameters

### -param pDesc [out]

Type: <b><a href="/windows/desktop/api/d3d11/ns-d3d11-d3d11_blend_desc">D3D11_BLEND_DESC</a>*</b>

A pointer to a <a href="/windows/desktop/api/d3d11/ns-d3d11-d3d11_blend_desc">D3D11_BLEND_DESC</a> structure that receives a description of the blend state.

## -remarks

You use the description for blending state in a call to the <a href="/windows/desktop/api/d3d11/nf-d3d11-id3d11device-createblendstate">ID3D11Device::CreateBlendState</a> method to create the blend-state object.

## -see-also

<a href="/windows/desktop/api/d3d11/nn-d3d11-id3d11blendstate">ID3D11BlendState</a>