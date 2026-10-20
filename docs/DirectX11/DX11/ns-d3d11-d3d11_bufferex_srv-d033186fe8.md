Source: [https://learn.microsoft.com/en-us/windows/win32/api/D3D11/ns-d3d11-d3d11_bufferex_srv](<https://learn.microsoft.com/en-us/windows/win32/api/D3D11/ns-d3d11-d3d11_bufferex_srv>)

# D3D11_BUFFEREX_SRV structure


## -description

Describes the elements in a raw buffer resource to use in a shader-resource view.

## -struct-fields

### -field FirstElement

Type: <b><a href="/windows/desktop/WinProg/windows-data-types">UINT</a></b>

The index of the first element to be accessed by the view.

### -field NumElements

Type: <b><a href="/windows/desktop/WinProg/windows-data-types">UINT</a></b>

The number of elements in the resource.

### -field Flags

Type: <b><a href="/windows/desktop/WinProg/windows-data-types">UINT</a></b>

A <a href="/windows/desktop/api/d3d11/ne-d3d11-d3d11_bufferex_srv_flag">D3D11_BUFFEREX_SRV_FLAG</a>-typed value that identifies view options for the buffer. Currently, the only option is to identify a raw view of the buffer. For more info about raw viewing of buffers, see <a href="/windows/desktop/direct3d11/overviews-direct3d-11-resources-intro">Raw Views of Buffers</a>.

## -remarks

This structure is used by <a href="/windows/desktop/api/d3d11/ns-d3d11-d3d11_shader_resource_view_desc">D3D11_SHADER_RESOURCE_VIEW_DESC</a> to create a raw view of a buffer.

## -see-also

<a href="/windows/desktop/direct3d11/d3d11-graphics-reference-resource-structures">Resource Structures</a>