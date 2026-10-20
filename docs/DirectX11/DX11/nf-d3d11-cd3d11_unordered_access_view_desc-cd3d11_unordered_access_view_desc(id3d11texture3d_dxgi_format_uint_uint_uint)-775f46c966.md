Source: [https://learn.microsoft.com/en-us/windows/win32/api/d3d11/nf-d3d11-cd3d11_unordered_access_view_desc-cd3d11_unordered_access_view_desc(id3d11texture3d_dxgi_format_uint_uint_uint)](<https://learn.microsoft.com/en-us/windows/win32/api/d3d11/nf-d3d11-cd3d11_unordered_access_view_desc-cd3d11_unordered_access_view_desc(id3d11texture3d_dxgi_format_uint_uint_uint)>)

# CD3D11_UNORDERED_ACCESS_VIEW_DESC::CD3D11_UNORDERED_ACCESS_VIEW_DESC(ID3D11Texture3D,DXGI_FORMAT,UINT,UINT,UINT)


## -description

Instantiates a new instance of a <a href="/previous-versions/windows/desktop/legacy/jj151712(v=vs.85)">CD3D11_UNORDERED_ACCESS_VIEW_DESC</a> structure that is initialized with 3D texture values.

## -parameters

### -param pTex3D

A pointer to a **ID3D11Texture3D** interface for a 3D texture.

### -param format

A **DXGI_FORMAT**-typed value that specifies the viewing format.

### -param mipSlice

The index of the mipmap level to use mip slice.

### -param firstWSlice

First depth level to use.

### -param wSize

Number of depth levels to use in the render-target view, starting from *firstWSlice*.
A value of -1 indicates all of the slices along the w axis, starting from *firstWSlice*.

## -see-also

<a href="/previous-versions/windows/desktop/legacy/jj151712(v=vs.85)">CD3D11_UNORDERED_ACCESS_VIEW_DESC</a>