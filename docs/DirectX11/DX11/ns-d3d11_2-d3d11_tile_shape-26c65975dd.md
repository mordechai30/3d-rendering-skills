Source: [https://learn.microsoft.com/en-us/windows/win32/api/D3D11_2/ns-d3d11_2-d3d11_tile_shape](<https://learn.microsoft.com/en-us/windows/win32/api/D3D11_2/ns-d3d11_2-d3d11_tile_shape>)

# D3D11_TILE_SHAPE structure


## -description

Describes the shape of a tile by specifying its dimensions.

## -struct-fields

### -field WidthInTexels

Type: <b><a href="/windows/desktop/WinProg/windows-data-types">UINT</a></b>

The width in texels of the tile.

### -field HeightInTexels

Type: <b><a href="/windows/desktop/WinProg/windows-data-types">UINT</a></b>

The height in texels of the tile.

### -field DepthInTexels

Type: <b><a href="/windows/desktop/WinProg/windows-data-types">UINT</a></b>

The depth in texels of the tile.

## -remarks

Texels are equivalent to pixels.  For untyped buffer resources, a texel is just a byte. For multisample antialiasing (MSAA) surfaces, the numbers are still in terms of pixels/texels.
The values here are independent of the surface dimensions.  Even if the surface is smaller than what would fit in a tile, the full tile dimensions are reported here.

## -see-also

<a href="/windows/desktop/direct3d11/d3d11-graphics-reference-resource-structures">Resource Structures</a>