Source: [https://learn.microsoft.com/en-us/windows/win32/api/D3D11_1/nf-d3d11_1-id3d11blendstate1-getdesc1](<https://learn.microsoft.com/en-us/windows/win32/api/D3D11_1/nf-d3d11_1-id3d11blendstate1-getdesc1>)

# ID3D11BlendState1::GetDesc1


## -description

Gets the description for blending state that you used to create the blend-state object.

## -parameters

### -param pDesc [out]

A pointer to a <a href="/windows/desktop/api/d3d11_1/ns-d3d11_1-cd3d11_blend_desc1">D3D11_BLEND_DESC1</a> structure that receives a description of the blend state. This blend state can specify logical operations as well as blending operations.

## -remarks

You use the description for blending state in a call to the <a href="/windows/desktop/api/d3d11_1/nf-d3d11_1-id3d11device1-createblendstate1">ID3D11Device1::CreateBlendState1</a> method to create the blend-state object.

## -see-also

<a href="/windows/desktop/api/d3d11_1/nn-d3d11_1-id3d11blendstate1">ID3D11BlendState1</a>