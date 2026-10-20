Source: [https://learn.microsoft.com/en-us/windows/win32/api/D3D11/ne-d3d11-d3d11_fill_mode](<https://learn.microsoft.com/en-us/windows/win32/api/D3D11/ne-d3d11-d3d11_fill_mode>)

# D3D11_FILL_MODE enumeration


## -description

Determines the fill mode to use when rendering triangles.

## -enum-fields

### -field D3D11_FILL_WIREFRAME:2

Draw lines connecting the vertices. Adjacent vertices are not drawn.

### -field D3D11_FILL_SOLID:3

Fill the triangles formed by the vertices. Adjacent vertices are not drawn.

## -remarks

This enumeration is part of a rasterizer-state object description (see <a href="/windows/desktop/api/d3d11/ns-d3d11-d3d11_rasterizer_desc">D3D11_RASTERIZER_DESC</a>).

## -see-also

<a href="/windows/desktop/direct3d11/d3d11-graphics-reference-d3d11-core-enums">Core Enumerations</a>