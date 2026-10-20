Source: [https://learn.microsoft.com/en-us/windows/win32/api/D3D11/nf-d3d11-id3d11devicecontext-resolvesubresource](<https://learn.microsoft.com/en-us/windows/win32/api/D3D11/nf-d3d11-id3d11devicecontext-resolvesubresource>)

# ID3D11DeviceContext::ResolveSubresource


## -description

Copy a multisampled resource into a non-multisampled resource.

## -parameters

### -param pDstResource [in]

Type: <b><a href="/windows/desktop/api/d3d11/nn-d3d11-id3d11resource">ID3D11Resource</a>*</b>

Destination resource. Must be a created with the <a href="/windows/desktop/api/d3d11/ne-d3d11-d3d11_usage">D3D11_USAGE_DEFAULT</a> flag and be single-sampled. See <a href="/windows/desktop/api/d3d11/nn-d3d11-id3d11resource">ID3D11Resource</a>.

### -param DstSubresource [in]

Type: <b><a href="/windows/desktop/WinProg/windows-data-types">UINT</a></b>

A zero-based index, that identifies the destination subresource. Use <a href="/windows/desktop/api/d3d11/nf-d3d11-d3d11calcsubresource">D3D11CalcSubresource</a> to calculate the index.

### -param pSrcResource [in]

Type: <b><a href="/windows/desktop/api/d3d11/nn-d3d11-id3d11resource">ID3D11Resource</a>*</b>

Source resource. Must be multisampled.

### -param SrcSubresource [in]

Type: <b><a href="/windows/desktop/WinProg/windows-data-types">UINT</a></b>

The source subresource of the source resource.

### -param Format [in]

Type: <b><a href="/windows/desktop/api/dxgiformat/ne-dxgiformat-dxgi_format">DXGI_FORMAT</a></b>

A <a href="/windows/desktop/api/dxgiformat/ne-dxgiformat-dxgi_format">DXGI_FORMAT</a> that indicates how the multisampled resource will be resolved to a single-sampled resource. 
      See remarks.

## -remarks

This API is most useful when re-using the resulting rendertarget of one render pass as an input to a second render pass.

The source and destination resources must be the same resource type and have the same dimensions. In addition, they must have compatible formats. There are three scenarios for this:

<table>
<tr>
<th>Scenario</th>
<th>Requirements</th>
</tr>
<tr>
<td>Source and destination are prestructured and typed</td>
<td>Both the source and destination must have identical formats and that format must be specified in the Format parameter.</td>
</tr>
<tr>
<td>One resource is prestructured and typed and the other is prestructured and typeless</td>
<td>The typed resource must have a format that is compatible with the typeless resource (i.e. the typed resource is DXGI_FORMAT_R32_FLOAT and the typeless resource is DXGI_FORMAT_R32_TYPELESS). The format of the typed resource must be specified in the Format parameter.</td>
</tr>
<tr>
<td>Source and destination are prestructured and typeless</td>
<td>Both the source and destination must have the same typeless format (i.e. both must have DXGI_FORMAT_R32_TYPELESS), and the Format parameter must specify a format that is compatible with the source and destination (i.e. if both are DXGI_FORMAT_R32_TYPELESS then DXGI_FORMAT_R32_FLOAT could be specified in the Format parameter).

For example, given the DXGI_FORMAT_R16G16B16A16_TYPELESS format:

<ul>
<li>The source (or dest) format could be DXGI_FORMAT_R16G16B16A16_UNORM</li>
<li>The dest (or source) format could be DXGI_FORMAT_R16G16B16A16_FLOAT</li>
</ul>
</td>
</tr>
</table>

## -see-also

<a href="/windows/desktop/api/d3d11/nn-d3d11-id3d11devicecontext">ID3D11DeviceContext</a>