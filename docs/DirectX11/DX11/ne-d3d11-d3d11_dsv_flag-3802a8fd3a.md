Source: [https://learn.microsoft.com/en-us/windows/win32/api/D3D11/ne-d3d11-d3d11_dsv_flag](<https://learn.microsoft.com/en-us/windows/win32/api/D3D11/ne-d3d11-d3d11_dsv_flag>)

# D3D11_DSV_FLAG enumeration


## -description

Depth-stencil view options.

## -enum-fields

### -field D3D11_DSV_READ_ONLY_DEPTH:0x1L

Indicates that depth values are read only.

### -field D3D11_DSV_READ_ONLY_STENCIL:0x2L

Indicates that stencil values are read only.

## -remarks

This enumeration is used by <a href="/windows/desktop/api/d3d11/ns-d3d11-d3d11_depth_stencil_view_desc">D3D11_DEPTH_STENCIL_VIEW_DESC</a>.

Limiting a depth-stencil buffer to read-only access allows more than one depth-stencil view to be bound to the pipeline simultaneously, since it is not possible to have a read/write conflicts between separate views.

## -see-also

<a href="/windows/desktop/direct3d11/d3d11-graphics-reference-resource-enums">Resource Enumerations</a>