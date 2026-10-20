Source: [https://learn.microsoft.com/en-us/windows/win32/api/D3D11/ns-d3d11-d3d11_unordered_access_view_desc](<https://learn.microsoft.com/en-us/windows/win32/api/D3D11/ns-d3d11-d3d11_unordered_access_view_desc>)

# D3D11_UNORDERED_ACCESS_VIEW_DESC structure


## -description

Specifies the subresources from a resource that are accessible using an unordered-access view.

## -struct-fields

### -field Format

Type: <b><a href="/windows/desktop/api/dxgiformat/ne-dxgiformat-dxgi_format">DXGI_FORMAT</a></b>

The data format (see <a href="/windows/desktop/api/dxgiformat/ne-dxgiformat-dxgi_format">DXGI_FORMAT</a>).

### -field ViewDimension

Type: <b><a href="/windows/desktop/api/d3d11/ne-d3d11-d3d11_uav_dimension">D3D11_UAV_DIMENSION</a></b>

The resource type (see <a href="/windows/desktop/api/d3d11/ne-d3d11-d3d11_uav_dimension">D3D11_UAV_DIMENSION</a>), which specifies how the resource will be accessed.

### -field Buffer

Type: <b><a href="/windows/desktop/api/d3d11/ns-d3d11-d3d11_buffer_uav">D3D11_BUFFER_UAV</a></b>

Specifies which buffer elements can be accessed (see <a href="/windows/desktop/api/d3d11/ns-d3d11-d3d11_buffer_uav">D3D11_BUFFER_UAV</a>).

### -field Texture1D

Type: <b><a href="/windows/desktop/api/d3d11/ns-d3d11-d3d11_tex1d_uav">D3D11_TEX1D_UAV</a></b>

Specifies the subresources in a 1D texture that can be accessed (see <a href="/windows/desktop/api/d3d11/ns-d3d11-d3d11_tex1d_uav">D3D11_TEX1D_UAV</a>).

### -field Texture1DArray

Type: <b><a href="/windows/desktop/api/d3d11/ns-d3d11-d3d11_tex1d_array_uav">D3D11_TEX1D_ARRAY_UAV</a></b>

Specifies the subresources in a 1D texture array that can be accessed (see <a href="/windows/desktop/api/d3d11/ns-d3d11-d3d11_tex1d_array_uav">D3D11_TEX1D_ARRAY_UAV</a>).

### -field Texture2D

Type: <b><a href="/windows/desktop/api/d3d11/ns-d3d11-d3d11_tex2d_uav">D3D11_TEX2D_UAV</a></b>

Specifies the subresources in a 2D texture that can be accessed (see <a href="/windows/desktop/api/d3d11/ns-d3d11-d3d11_tex2d_uav">D3D11_TEX2D_UAV</a>).

### -field Texture2DArray

Type: <b><a href="/windows/desktop/api/d3d11/ns-d3d11-d3d11_tex2d_array_uav">D3D11_TEX2D_ARRAY_UAV</a></b>

Specifies the subresources in a 2D texture array that can be accessed (see <a href="/windows/desktop/api/d3d11/ns-d3d11-d3d11_tex2d_array_uav">D3D11_TEX2D_ARRAY_UAV</a>).

### -field Texture3D

Type: <b><a href="/windows/desktop/api/d3d11/ns-d3d11-d3d11_tex3d_uav">D3D11_TEX3D_UAV</a></b>

Specifies subresources in a 3D texture that can be accessed (see <a href="/windows/desktop/api/d3d11/ns-d3d11-d3d11_tex3d_uav">D3D11_TEX3D_UAV</a>).

## -remarks

An unordered-access-view description is passed into <a href="/windows/desktop/api/d3d11/nf-d3d11-id3d11device-createunorderedaccessview">ID3D11Device::CreateUnorderedAccessView</a> to create a view.

## -see-also

<a href="/windows/desktop/direct3d11/d3d11-graphics-reference-resource-structures">Resource Structures</a>