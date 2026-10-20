Source: [https://learn.microsoft.com/en-us/windows/win32/api/D3D11/ns-d3d11-d3d11_tex3d_rtv](<https://learn.microsoft.com/en-us/windows/win32/api/D3D11/ns-d3d11-d3d11_tex3d_rtv>)

# D3D11_TEX3D_RTV structure


## -description

Specifies the subresources from a 3D texture to use in a render-target view.

## -struct-fields

### -field MipSlice

Type: <b><a href="/windows/desktop/WinProg/windows-data-types">UINT</a></b>

The index of the mipmap level to use mip slice.

### -field FirstWSlice

Type: <b><a href="/windows/desktop/WinProg/windows-data-types">UINT</a></b>

First depth level to use.

### -field WSize

Type: <b><a href="/windows/desktop/WinProg/windows-data-types">UINT</a></b>

Number of depth levels to use in the render-target view, starting from <b>FirstWSlice</b>. A value of -1 indicates all of the slices along the w axis, starting from <b>FirstWSlice</b>.

## -remarks

This structure is one member of a render target view. See <a href="/windows/desktop/api/d3d11/ns-d3d11-d3d11_render_target_view_desc">D3D11_RENDER_TARGET_VIEW_DESC</a>.

## -see-also

<a href="/windows/desktop/direct3d11/d3d11-graphics-reference-resource-structures">Resource Structures</a>