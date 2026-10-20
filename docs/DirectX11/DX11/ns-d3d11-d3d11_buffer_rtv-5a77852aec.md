Source: [https://learn.microsoft.com/en-us/windows/win32/api/D3D11/ns-d3d11-d3d11_buffer_rtv](<https://learn.microsoft.com/en-us/windows/win32/api/D3D11/ns-d3d11-d3d11_buffer_rtv>)

# D3D11_BUFFER_RTV structure


## -description

Specifies the elements in a buffer resource to use in a render-target view.

## -struct-fields

### -field FirstElement

Type: <b><a href="/windows/desktop/WinProg/windows-data-types">UINT</a></b>

Number of bytes between the beginning of the buffer and the first element to access.

### -field ElementOffset

Type: <b><a href="/windows/desktop/WinProg/windows-data-types">UINT</a></b>

The offset of the first element in the view to access, relative to element 0.

### -field NumElements

Type: <b><a href="/windows/desktop/WinProg/windows-data-types">UINT</a></b>

The total number of elements in the view.

### -field ElementWidth

Type: <b><a href="/windows/desktop/WinProg/windows-data-types">UINT</a></b>

The width of each element (in bytes). This can be determined from the format stored in the render-target-view description.

## -remarks

A render-target view is a member of a render-target-view description (see <a href="/windows/desktop/api/d3d11/ns-d3d11-d3d11_render_target_view_desc">D3D11_RENDER_TARGET_VIEW_DESC</a>). Create a render-target view by calling <a href="/windows/desktop/api/d3d11/nf-d3d11-id3d11device-createrendertargetview">ID3D11Device::CreateRenderTargetView</a>.

## -see-also

<a href="/windows/desktop/direct3d11/d3d11-graphics-reference-resource-structures">Resource Structures</a>