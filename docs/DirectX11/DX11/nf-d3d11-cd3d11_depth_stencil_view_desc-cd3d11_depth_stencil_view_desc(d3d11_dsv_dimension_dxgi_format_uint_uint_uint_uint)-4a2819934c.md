Source: [https://learn.microsoft.com/en-us/windows/win32/api/d3d11/nf-d3d11-cd3d11_depth_stencil_view_desc-cd3d11_depth_stencil_view_desc(d3d11_dsv_dimension_dxgi_format_uint_uint_uint_uint)](<https://learn.microsoft.com/en-us/windows/win32/api/d3d11/nf-d3d11-cd3d11_depth_stencil_view_desc-cd3d11_depth_stencil_view_desc(d3d11_dsv_dimension_dxgi_format_uint_uint_uint_uint)>)

# CD3D11_DEPTH_STENCIL_VIEW_DESC::CD3D11_DEPTH_STENCIL_VIEW_DESC(D3D11_DSV_DIMENSION,DXGI_FORMAT,UINT,UINT,UINT,UINT)


## -description

Instantiates a new instance of a <a href="/previous-versions/windows/desktop/legacy/jj151639(v=vs.85)">CD3D11_DEPTH_STENCIL_VIEW_DESC</a> structure that is initialized with <a href="/windows/desktop/api/d3d11/ns-d3d11-d3d11_depth_stencil_view_desc">D3D11_DEPTH_STENCIL_VIEW_DESC</a> values.

## -parameters

### -param viewDimension

Type: <b><a href="/windows/desktop/api/d3d11/ne-d3d11-d3d11_dsv_dimension">D3D11_DSV_DIMENSION</a></b>

A <a href="/windows/desktop/api/d3d11/ne-d3d11-d3d11_dsv_dimension">D3D11_DSV_DIMENSION</a>-typed value that specifies the depth-stencil type of the view.

### -param format

Type: <b><a href="/windows/desktop/api/dxgiformat/ne-dxgiformat-dxgi_format">DXGI_FORMAT</a></b>

A <a href="/windows/desktop/api/dxgiformat/ne-dxgiformat-dxgi_format">DXGI_FORMAT</a>-typed value that specifies the viewing format.

### -param mipSlice

Type: <b><a href="/windows/desktop/WinProg/windows-data-types">UINT</a></b>

The index of the mipmap level to use mip slice.

### -param firstArraySlice

Type: <b><a href="/windows/desktop/WinProg/windows-data-types">UINT</a></b>

The index of the first element to use in an array of elements.

### -param arraySize

Type: <b><a href="/windows/desktop/WinProg/windows-data-types">UINT</a></b>

Number of elements in the array.

### -param flags

Type: <b><a href="/windows/desktop/WinProg/windows-data-types">UINT</a></b>

A value that describes whether the texture is read only.  Pass 0 to specify that it is not read only; otherwise, pass one of the members of 
        the <a href="/windows/desktop/api/d3d11/ne-d3d11-d3d11_dsv_flag">D3D11_DSV_FLAG</a> enumerated type.

## -see-also

<a href="/previous-versions/windows/desktop/legacy/jj151639(v=vs.85)">CD3D11_DEPTH_STENCIL_VIEW_DESC</a>