Source: [https://learn.microsoft.com/en-us/windows/win32/api/D3D11/ns-d3d11-d3d11_tex3d_uav](<https://learn.microsoft.com/en-us/windows/win32/api/D3D11/ns-d3d11-d3d11_tex3d_uav>)

# D3D11_TEX3D_UAV structure


## -description

Describes a unordered-access 3D texture resource.

## -struct-fields

### -field MipSlice

Type: <b><a href="/windows/desktop/WinProg/windows-data-types">UINT</a></b>

The mipmap slice index.

### -field FirstWSlice

Type: <b><a href="/windows/desktop/WinProg/windows-data-types">UINT</a></b>

The zero-based index of the first depth slice to be accessed.

### -field WSize

Type: <b><a href="/windows/desktop/WinProg/windows-data-types">UINT</a></b>

The number of depth slices.

## -remarks

This structure is used by a <a href="/windows/desktop/api/d3d11/ns-d3d11-d3d11_unordered_access_view_desc">D3D11_UNORDERED_ACCESS_VIEW_DESC</a>.

## -see-also

<a href="/windows/desktop/direct3d11/d3d11-graphics-reference-resource-structures">Resource Structures</a>