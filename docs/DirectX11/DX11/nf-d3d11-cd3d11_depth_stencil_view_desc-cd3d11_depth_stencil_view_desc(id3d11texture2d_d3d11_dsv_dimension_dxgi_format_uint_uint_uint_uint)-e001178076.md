Source: [https://learn.microsoft.com/en-us/windows/win32/api/d3d11/nf-d3d11-cd3d11_depth_stencil_view_desc-cd3d11_depth_stencil_view_desc(id3d11texture2d_d3d11_dsv_dimension_dxgi_format_uint_uint_uint_uint)](<https://learn.microsoft.com/en-us/windows/win32/api/d3d11/nf-d3d11-cd3d11_depth_stencil_view_desc-cd3d11_depth_stencil_view_desc(id3d11texture2d_d3d11_dsv_dimension_dxgi_format_uint_uint_uint_uint)>)

# CD3D11_DEPTH_STENCIL_VIEW_DESC::CD3D11_DEPTH_STENCIL_VIEW_DESC(ID3D11Texture2D,D3D11_DSV_DIMENSION,DXGI_FORMAT,UINT,UINT,UINT,UINT)


## -description

Instantiates a new instance of a <a href="/previous-versions/windows/desktop/legacy/jj151639(v=vs.85)">CD3D11_DEPTH_STENCIL_VIEW_DESC</a> structure that is initialized with 2D texture values.

## -parameters

### -param pTex2D

A pointer to a **ID3D11Texture2D**.

### -param viewDimension

A **D3D11_DSV_DIMENSION**-typed value that specifies the depth-stencil type of the view.

### -param format

A **DXGI_FORMAT**-typed value that specifies the viewing format.

### -param mipSlice

The index of the mipmap level to use mip slice.

### -param firstArraySlice

The index of the first element to use in an array of elements.

### -param arraySize

Number of elements in the array.

### -param flags

A value that describes whether the texture is read only.
Pass 0 to specify that it is not read only; otherwise, pass one of the members of the **D3D11_DSV_FLAG** enumerated type.

## -see-also

<a href="/previous-versions/windows/desktop/legacy/jj151639(v=vs.85)">CD3D11_DEPTH_STENCIL_VIEW_DESC</a>