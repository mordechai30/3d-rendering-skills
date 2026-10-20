Source: [https://learn.microsoft.com/en-us/windows/win32/api/D3D11_3/ns-d3d11_3-cd3d11_unordered_access_view_desc1](<https://learn.microsoft.com/en-us/windows/win32/api/D3D11_3/ns-d3d11_3-cd3d11_unordered_access_view_desc1>)

# CD3D11_UNORDERED_ACCESS_VIEW_DESC1 structure


## -description

Describes the subresources from a resource that are accessible using an unordered-access view.

## -struct-fields

### -field CD3D11_UNORDERED_ACCESS_VIEW_DESC1

TBD

### -field ~CD3D11_UNORDERED_ACCESS_VIEW_DESC1

TBD

### -field operator const D3D11_UNORDERED_ACCESS_VIEW_DESC1&

TBD

### -field D3D11_UNORDERED_ACCESS_VIEW_DESC1

 




#### - Buffer

A <a href="/windows/desktop/api/d3d11/ns-d3d11-d3d11_buffer_uav">D3D11_BUFFER_UAV</a> structure that specifies which buffer elements can be accessed.


#### - Format

A <a href="/windows/desktop/api/dxgiformat/ne-dxgiformat-dxgi_format">DXGI_FORMAT</a>-typed value that specifies the data format.


#### - Texture1D

A <a href="/windows/desktop/api/d3d11/ns-d3d11-d3d11_tex1d_uav">D3D11_TEX1D_UAV</a> structure that specifies the subresources in a 1D texture that can be accessed.


#### - Texture1DArray

A <a href="/windows/desktop/api/d3d11/ns-d3d11-d3d11_tex1d_array_uav">D3D11_TEX1D_ARRAY_UAV</a> structure that specifies the subresources in a 1D texture array that can be accessed.


#### - Texture2D

A <a href="/windows/desktop/api/d3d11_3/ns-d3d11_3-d3d11_tex2d_uav1">D3D11_TEX2D_UAV1</a> structure that specifies the subresources in a 2D texture that can be accessed.


#### - Texture2DArray

A <a href="/windows/desktop/api/d3d11_3/ns-d3d11_3-d3d11_tex2d_array_uav1">D3D11_TEX2D_ARRAY_UAV1</a> structure that specifies the subresources in a 2D texture array that can be accessed.


#### - Texture3D

A <a href="/windows/desktop/api/d3d11/ns-d3d11-d3d11_tex3d_uav">D3D11_TEX3D_UAV</a> structure that specifies subresources in a 3D texture that can be accessed.


#### - ViewDimension

A <a href="/windows/desktop/api/d3d11/ne-d3d11-d3d11_uav_dimension">D3D11_UAV_DIMENSION</a>-typed value that  specifies the resource type of the view. This type is the same as the resource type of the underlying resource. This member also determines which _UAV to use in the union below.

## -remarks

An unordered-access-view description is passed into <a href="/windows/desktop/api/d3d11_3/nf-d3d11_3-id3d11device3-createunorderedaccessview1">ID3D11Device3::CreateUnorderedAccessView1</a> to create a view.

## -see-also

<a href="/windows/desktop/direct3d11/d3d11-graphics-reference-resource-structures">Resource Structures</a>