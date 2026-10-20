Source: [https://learn.microsoft.com/en-us/windows/win32/api/D3D11/ne-d3d11-d3d11_cull_mode](<https://learn.microsoft.com/en-us/windows/win32/api/D3D11/ne-d3d11-d3d11_cull_mode>)

# D3D11_CULL_MODE enumeration


## -description

Indicates triangles facing a particular direction are not drawn.

## -enum-fields

### -field D3D11_CULL_NONE:1

Always draw all triangles.

### -field D3D11_CULL_FRONT:2

Do not draw triangles that are front-facing.

### -field D3D11_CULL_BACK:3

Do not draw triangles that are back-facing.

## -remarks

This enumeration is part of a rasterizer-state object description (see <a href="/windows/desktop/api/d3d11/ns-d3d11-d3d11_rasterizer_desc">D3D11_RASTERIZER_DESC</a>).

## -see-also

<a href="/windows/desktop/direct3d11/d3d11-graphics-reference-d3d11-core-enums">Core Enumerations</a>