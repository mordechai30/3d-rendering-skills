Source: [https://learn.microsoft.com/en-us/windows/win32/api/d3d11/nf-d3d11-cd3d11_unordered_access_view_desc-cd3d11_unordered_access_view_desc(d3d11_uav_dimension_dxgi_format_uint_uint_uint_uint)](<https://learn.microsoft.com/en-us/windows/win32/api/d3d11/nf-d3d11-cd3d11_unordered_access_view_desc-cd3d11_unordered_access_view_desc(d3d11_uav_dimension_dxgi_format_uint_uint_uint_uint)>)

# CD3D11_UNORDERED_ACCESS_VIEW_DESC::CD3D11_UNORDERED_ACCESS_VIEW_DESC(D3D11_UAV_DIMENSION,DXGI_FORMAT,UINT,UINT,UINT,UINT)


## -description

Instantiates a new instance of a <a href="/previous-versions/windows/desktop/legacy/jj151712(v=vs.85)">CD3D11_UNORDERED_ACCESS_VIEW_DESC</a> structure that is initialized with <a href="/windows/desktop/api/d3d11/ns-d3d11-d3d11_unordered_access_view_desc">D3D11_UNORDERED_ACCESS_VIEW_DESC</a> values.

## -parameters

### -param viewDimension

Type: <b><a href="/windows/desktop/api/d3d11/ne-d3d11-d3d11_uav_dimension">D3D11_UAV_DIMENSION</a></b>

A <a href="/windows/desktop/api/d3d11/ne-d3d11-d3d11_uav_dimension">D3D11_UAV_DIMENSION</a>-typed value that specifies the resource type of the view.

### -param format

Type: <b><a href="/windows/desktop/api/dxgiformat/ne-dxgiformat-dxgi_format">DXGI_FORMAT</a></b>

A <a href="/windows/desktop/api/dxgiformat/ne-dxgiformat-dxgi_format">DXGI_FORMAT</a>-typed value that specifies the viewing format.

### -param mipSlice

Type: <b><a href="/windows/desktop/WinProg/windows-data-types">UINT</a></b>

The index of the mipmap level to use mip slice. <b>FirstElement</b> for <a href="/windows/desktop/api/d3d11/ns-d3d11-d3d11_buffer_uav">D3D11_BUFFER_UAV</a>.

### -param firstArraySlice

Type: <b><a href="/windows/desktop/WinProg/windows-data-types">UINT</a></b>

The index of the first element to use in an array of elements.

<b>NumElements</b> for <a href="/windows/desktop/api/d3d11/ns-d3d11-d3d11_buffer_uav">D3D11_BUFFER_UAV</a>. <b>FirstWSlice</b> for <a href="/windows/desktop/api/d3d11/ns-d3d11-d3d11_tex3d_uav">D3D11_TEX3D_UAV</a>.

### -param arraySize

Type: <b><a href="/windows/desktop/WinProg/windows-data-types">UINT</a></b>

Number of elements in the array. <b>WSize</b> for <a href="/windows/desktop/api/d3d11/ns-d3d11-d3d11_tex3d_uav">D3D11_TEX3D_UAV</a>.

### -param flags

Type: <b><a href="/windows/desktop/WinProg/windows-data-types">UINT</a></b>

A <a href="/windows/desktop/api/d3d11/ne-d3d11-d3d11_buffer_uav_flag">D3D11_BUFFER_UAV_FLAG</a>-typed value that identifies view options for a buffer. For <a href="/windows/desktop/api/d3d11/ns-d3d11-d3d11_buffer_uav">D3D11_BUFFER_UAV</a> only.

## -see-also

<a href="/previous-versions/windows/desktop/legacy/jj151712(v=vs.85)">CD3D11_UNORDERED_ACCESS_VIEW_DESC</a>