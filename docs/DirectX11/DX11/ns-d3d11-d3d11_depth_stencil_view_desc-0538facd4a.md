Source: [https://learn.microsoft.com/en-us/windows/win32/api/D3D11/ns-d3d11-d3d11_depth_stencil_view_desc](<https://learn.microsoft.com/en-us/windows/win32/api/D3D11/ns-d3d11-d3d11_depth_stencil_view_desc>)

# D3D11_DEPTH_STENCIL_VIEW_DESC structure


## -description

Specifies the subresources of a texture that are accessible from a depth-stencil view.

## -struct-fields

### -field Format

Type: <b><a href="/windows/desktop/api/dxgiformat/ne-dxgiformat-dxgi_format">DXGI_FORMAT</a></b>

Resource data  format (see <a href="/windows/desktop/api/dxgiformat/ne-dxgiformat-dxgi_format">DXGI_FORMAT</a>). See remarks for allowable formats.

### -field ViewDimension

Type: <b><a href="/windows/desktop/api/d3d11/ne-d3d11-d3d11_dsv_dimension">D3D11_DSV_DIMENSION</a></b>

Type of resource (see <a href="/windows/desktop/api/d3d11/ne-d3d11-d3d11_dsv_dimension">D3D11_DSV_DIMENSION</a>). Specifies how a depth-stencil resource will be accessed; the value is stored in the 
        union in this structure.

### -field Flags

Type: <b><a href="/windows/desktop/WinProg/windows-data-types">UINT</a></b>

A value that describes whether the texture is read only.  Pass 0 to specify that it is not read only; otherwise, pass one of the members of 
        the <a href="/windows/desktop/api/d3d11/ne-d3d11-d3d11_dsv_flag">D3D11_DSV_FLAG</a> enumerated type.

### -field Texture1D

Type: <b><a href="/windows/desktop/api/d3d11/ns-d3d11-d3d11_tex1d_dsv">D3D11_TEX1D_DSV</a></b>

Specifies a 1D texture subresource (see <a href="/windows/desktop/api/d3d11/ns-d3d11-d3d11_tex1d_dsv">D3D11_TEX1D_DSV</a>).

### -field Texture1DArray

Type: <b><a href="/windows/desktop/api/d3d11/ns-d3d11-d3d11_tex1d_array_dsv">D3D11_TEX1D_ARRAY_DSV</a></b>

Specifies an array of 1D texture subresources (see <a href="/windows/desktop/api/d3d11/ns-d3d11-d3d11_tex1d_array_dsv">D3D11_TEX1D_ARRAY_DSV</a>).

### -field Texture2D

Type: <b><a href="/windows/desktop/api/d3d11/ns-d3d11-d3d11_tex2d_dsv">D3D11_TEX2D_DSV</a></b>

Specifies a 2D texture subresource (see <a href="/windows/desktop/api/d3d11/ns-d3d11-d3d11_tex2d_dsv">D3D11_TEX2D_DSV</a>).

### -field Texture2DArray

Type: <b><a href="/windows/desktop/api/d3d11/ns-d3d11-d3d11_tex2d_array_dsv">D3D11_TEX2D_ARRAY_DSV</a></b>

Specifies an array of 2D texture subresources (see <a href="/windows/desktop/api/d3d11/ns-d3d11-d3d11_tex2d_array_dsv">D3D11_TEX2D_ARRAY_DSV</a>).

### -field Texture2DMS

Type: <b><a href="/windows/desktop/api/d3d11/ns-d3d11-d3d11_tex2dms_dsv">D3D11_TEX2DMS_DSV</a></b>

Specifies a multisampled 2D texture (see <a href="/windows/desktop/api/d3d11/ns-d3d11-d3d11_tex2dms_dsv">D3D11_TEX2DMS_DSV</a>).

### -field Texture2DMSArray

Type: <b><a href="/windows/desktop/api/d3d11/ns-d3d11-d3d11_tex2dms_array_dsv">D3D11_TEX2DMS_ARRAY_DSV</a></b>

Specifies an array of multisampled 2D textures (see <a href="/windows/desktop/api/d3d11/ns-d3d11-d3d11_tex2dms_array_dsv">D3D11_TEX2DMS_ARRAY_DSV</a>).

## -remarks

These are valid formats for a depth-stencil view:

<ul>
<li>DXGI_FORMAT_D16_UNORM</li>
<li>DXGI_FORMAT_D24_UNORM_S8_UINT</li>
<li>DXGI_FORMAT_D32_FLOAT</li>
<li>DXGI_FORMAT_D32_FLOAT_S8X24_UINT</li>
<li>DXGI_FORMAT_UNKNOWN</li>
</ul>
A depth-stencil view cannot use a typeless format.  If the format chosen is DXGI_FORMAT_UNKNOWN, then the format of the parent resource is used.

A depth-stencil-view description is needed when calling <a href="/windows/desktop/api/d3d11/nf-d3d11-id3d11device-createdepthstencilview">ID3D11Device::CreateDepthStencilView</a>.

## -see-also

<a href="/windows/desktop/direct3d11/d3d11-graphics-reference-resource-structures">Resource Structures</a>