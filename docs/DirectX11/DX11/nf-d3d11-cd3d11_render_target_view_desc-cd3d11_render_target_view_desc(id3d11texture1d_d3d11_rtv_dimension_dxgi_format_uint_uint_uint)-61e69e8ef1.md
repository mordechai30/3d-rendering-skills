Source: [https://learn.microsoft.com/en-us/windows/win32/api/d3d11/nf-d3d11-cd3d11_render_target_view_desc-cd3d11_render_target_view_desc(id3d11texture1d_d3d11_rtv_dimension_dxgi_format_uint_uint_uint)](<https://learn.microsoft.com/en-us/windows/win32/api/d3d11/nf-d3d11-cd3d11_render_target_view_desc-cd3d11_render_target_view_desc(id3d11texture1d_d3d11_rtv_dimension_dxgi_format_uint_uint_uint)>)

# CD3D11_RENDER_TARGET_VIEW_DESC::CD3D11_RENDER_TARGET_VIEW_DESC(ID3D11Texture1D,D3D11_RTV_DIMENSION,DXGI_FORMAT,UINT,UINT,UINT)


## -description

Instantiates a new instance of a <a href="/previous-versions/windows/desktop/legacy/jj151668(v=vs.85)">CD3D11_RENDER_TARGET_VIEW_DESC</a> structure that is initialized with **D3D11_TEX1D_RTV** or **D3D11_TEX1D_ARRAY_RTV** values.

## -parameters

### -param pTex1D

A pointer to a **ID3D11Texture1D** interface for a 1D texture.

### -param viewDimension

A **D3D11_RTV_DIMENSION**-typed value that specifies the resource type of the view.

### -param format

A **DXGI_FORMAT**-typed value that specifies the viewing format.

### -param mipSlice

The index of the mipmap level to use mip slice.

### -param firstArraySlice

The index of the first element to use in an array of elements.

### -param arraySize

Number of elements in the array.

## -see-also

<a href="/previous-versions/windows/desktop/legacy/jj151668(v=vs.85)">CD3D11_RENDER_TARGET_VIEW_DESC</a>