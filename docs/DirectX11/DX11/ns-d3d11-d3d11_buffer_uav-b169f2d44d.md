Source: [https://learn.microsoft.com/en-us/windows/win32/api/D3D11/ns-d3d11-d3d11_buffer_uav](<https://learn.microsoft.com/en-us/windows/win32/api/D3D11/ns-d3d11-d3d11_buffer_uav>)

# D3D11_BUFFER_UAV structure


## -description

Describes the elements in a buffer to use in a unordered-access view.

## -struct-fields

### -field FirstElement

Type: <b><a href="/windows/desktop/WinProg/windows-data-types">UINT</a></b>

The zero-based index of the first element to be accessed.

### -field NumElements

Type: <b><a href="/windows/desktop/WinProg/windows-data-types">UINT</a></b>

The number of elements in the resource. For structured buffers, this is the number of structures in the buffer.

### -field Flags

Type: <b><a href="/windows/desktop/WinProg/windows-data-types">UINT</a></b>

View options for the resource (see <a href="/windows/desktop/api/d3d11/ne-d3d11-d3d11_buffer_uav_flag">D3D11_BUFFER_UAV_FLAG</a>).

## -remarks

This structure is used by a <a href="/windows/desktop/api/d3d11/ns-d3d11-d3d11_unordered_access_view_desc">D3D11_UNORDERED_ACCESS_VIEW_DESC</a>.

## -see-also

<a href="/windows/desktop/direct3d11/d3d11-graphics-reference-resource-structures">Resource Structures</a>