Source: [https://learn.microsoft.com/en-us/windows/win32/api/D3D11/nf-d3d11-id3d11devicecontext-cssetsamplers](<https://learn.microsoft.com/en-us/windows/win32/api/D3D11/nf-d3d11-id3d11devicecontext-cssetsamplers>)

# ID3D11DeviceContext::CSSetSamplers


## -description

Set an array of sampler states to the compute-shader stage.

## -parameters

### -param StartSlot [in]

Type: <b><a href="/windows/desktop/WinProg/windows-data-types">UINT</a></b>

Index into the device's zero-based array to begin setting samplers to (ranges from 0 to D3D11_COMMONSHADER_SAMPLER_SLOT_COUNT - 1).

### -param NumSamplers [in]

Type: <b><a href="/windows/desktop/WinProg/windows-data-types">UINT</a></b>

Number of samplers in the array. Each pipeline stage has a total of 16 sampler slots available (ranges from 0 to D3D11_COMMONSHADER_SAMPLER_SLOT_COUNT - StartSlot).

### -param ppSamplers [in, optional]

Type: <b><a href="/windows/desktop/api/d3d11/nn-d3d11-id3d11samplerstate">ID3D11SamplerState</a>*</b>

Pointer to an array of sampler-state interfaces (see <a href="/windows/desktop/api/d3d11/nn-d3d11-id3d11samplerstate">ID3D11SamplerState</a>). See Remarks.

## -remarks

Any sampler may be set to <b>NULL</b>; this invokes the default state, which is defined to be the following.


```
//Default sampler state:
D3D11_SAMPLER_DESC SamplerDesc;
SamplerDesc.Filter = D3D11_FILTER_MIN_MAG_MIP_LINEAR;
SamplerDesc.AddressU = D3D11_TEXTURE_ADDRESS_CLAMP;
SamplerDesc.AddressV = D3D11_TEXTURE_ADDRESS_CLAMP;
SamplerDesc.AddressW = D3D11_TEXTURE_ADDRESS_CLAMP;
SamplerDesc.MipLODBias = 0;
SamplerDesc.MaxAnisotropy = 1;
SamplerDesc.ComparisonFunc = D3D11_COMPARISON_NEVER;
SamplerDesc.BorderColor[0] = 1.0f;
SamplerDesc.BorderColor[1] = 1.0f;
SamplerDesc.BorderColor[2] = 1.0f;
SamplerDesc.BorderColor[3] = 1.0f;
SamplerDesc.MinLOD = -FLT_MAX;
SamplerDesc.MaxLOD = FLT_MAX;
		
```


The method will hold a reference to the interfaces passed in.
      This differs from the device state behavior in Direct3D 10.

## -see-also

<a href="/windows/desktop/api/d3d11/nn-d3d11-id3d11devicecontext">ID3D11DeviceContext</a>