Source: [https://learn.microsoft.com/en-us/windows/win32/api/D3D11/nf-d3d11-id3d11samplerstate-getdesc](<https://learn.microsoft.com/en-us/windows/win32/api/D3D11/nf-d3d11-id3d11samplerstate-getdesc>)

# ID3D11SamplerState::GetDesc


## -description

Gets the description for sampler state that you used to create the sampler-state object.

## -parameters

### -param pDesc [out]

Type: <b><a href="/windows/desktop/api/d3d11/ns-d3d11-d3d11_sampler_desc">D3D11_SAMPLER_DESC</a>*</b>

A pointer to a <a href="/windows/desktop/api/d3d11/ns-d3d11-d3d11_sampler_desc">D3D11_SAMPLER_DESC</a> structure that receives a description of the sampler state.

## -remarks

You use the description for sampler state in a call to the <a href="/windows/desktop/api/d3d11/nf-d3d11-id3d11device-createsamplerstate">ID3D11Device::CreateSamplerState</a> method to create the sampler-state object.

## -see-also

<a href="/windows/desktop/api/d3d11/nn-d3d11-id3d11samplerstate">ID3D11SamplerState</a>