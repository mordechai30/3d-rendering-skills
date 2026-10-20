Source: [https://learn.microsoft.com/en-us/windows/win32/api/D3D11/ns-d3d11-d3d11_tex1d_array_dsv](<https://learn.microsoft.com/en-us/windows/win32/api/D3D11/ns-d3d11-d3d11_tex1d_array_dsv>)

# D3D11_TEX1D_ARRAY_DSV structure


## -description

Specifies the subresources from an array of 1D textures to use in a depth-stencil view.

## -struct-fields

### -field MipSlice

Type: <b><a href="/windows/desktop/WinProg/windows-data-types">UINT</a></b>

The index of the first mipmap level to use.

### -field FirstArraySlice

Type: <b><a href="/windows/desktop/WinProg/windows-data-types">UINT</a></b>

The index of the first texture to use in an array of textures.

### -field ArraySize

Type: <b><a href="/windows/desktop/WinProg/windows-data-types">UINT</a></b>

Number of textures to use.

## -remarks

This structure is one member of a depth-stencil-view description (see <a href="/windows/desktop/api/d3d11/ns-d3d11-d3d11_depth_stencil_view_desc">D3D11_DEPTH_STENCIL_VIEW_DESC</a>).

## -see-also

<a href="/windows/desktop/direct3d11/d3d11-graphics-reference-resource-structures">Resource Structures</a>