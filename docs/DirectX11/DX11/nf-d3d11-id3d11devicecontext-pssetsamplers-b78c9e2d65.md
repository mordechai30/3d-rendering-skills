Source: [https://learn.microsoft.com/en-us/windows/win32/api/D3D11/nf-d3d11-id3d11devicecontext-pssetsamplers](<https://learn.microsoft.com/en-us/windows/win32/api/D3D11/nf-d3d11-id3d11devicecontext-pssetsamplers>)

# ID3D11DeviceContext::PSSetSamplers


## -description

Set an array of sampler states to the pixel shader pipeline stage.

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

<table>
<tr>
<th>State</th>
<th>Default Value</th>
</tr>
<tr>
<td>Filter</td>
<td>D3D11_FILTER_MIN_MAG_MIP_LINEAR</td>
</tr>
<tr>
<td>AddressU</td>
<td>D3D11_TEXTURE_ADDRESS_CLAMP</td>
</tr>
<tr>
<td>AddressV</td>
<td>D3D11_TEXTURE_ADDRESS_CLAMP</td>
</tr>
<tr>
<td>AddressW</td>
<td>D3D11_TEXTURE_ADDRESS_CLAMP</td>
</tr>
<tr>
<td>MipLODBias</td>
<td>0</td>
</tr>
<tr>
<td>MaxAnisotropy</td>
<td>1</td>
</tr>
<tr>
<td>ComparisonFunc</td>
<td>D3D11_COMPARISON_NEVER</td>
</tr>
<tr>
<td>BorderColor[0]</td>
<td>1.0f</td>
</tr>
<tr>
<td>BorderColor[1]</td>
<td>1.0f</td>
</tr>
<tr>
<td>BorderColor[2]</td>
<td>1.0f</td>
</tr>
<tr>
<td>BorderColor[3]</td>
<td>1.0f</td>
</tr>
<tr>
<td>MinLOD</td>
<td>-FLT_MAX</td>
</tr>
<tr>
<td>MaxLOD</td>
<td>FLT_MAX</td>
</tr>
</table>
 

The method will hold a reference to the interfaces passed in.
      This differs from the device state behavior in Direct3D 10.

## -see-also

<a href="/windows/desktop/api/d3d11/nn-d3d11-id3d11devicecontext">ID3D11DeviceContext</a>