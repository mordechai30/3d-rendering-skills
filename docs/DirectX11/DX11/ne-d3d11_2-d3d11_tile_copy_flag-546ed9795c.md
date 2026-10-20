Source: [https://learn.microsoft.com/en-us/windows/win32/api/D3D11_2/ne-d3d11_2-d3d11_tile_copy_flag](<https://learn.microsoft.com/en-us/windows/win32/api/D3D11_2/ne-d3d11_2-d3d11_tile_copy_flag>)

# D3D11_TILE_COPY_FLAG enumeration


## -description

Identifies how to copy a tile.

## -enum-fields

### -field D3D11_TILE_COPY_NO_OVERWRITE:0x1

Indicates that the GPU isn't currently referencing any of the 
 portions of destination memory being written.

### -field D3D11_TILE_COPY_LINEAR_BUFFER_TO_SWIZZLED_TILED_RESOURCE:0x2

Indicates that the <a href="/windows/desktop/api/d3d11_2/nf-d3d11_2-id3d11devicecontext2-copytiles">ID3D11DeviceContext2::CopyTiles</a> operation involves copying a linear buffer to a swizzled tiled resource. This means to copy tile data from the 
specified buffer location, reading tiles sequentially,
to the specified tile region (in x,y,z order if the region is a box), swizzling to optimal hardware memory layout as needed.
In this <b>ID3D11DeviceContext2::CopyTiles</b> call, you specify the source data with the  <i>pBuffer</i> parameter and the destination with the <i>pTiledResource</i> parameter.

### -field D3D11_TILE_COPY_SWIZZLED_TILED_RESOURCE_TO_LINEAR_BUFFER:0x4

Indicates that the <a href="/windows/desktop/api/d3d11_2/nf-d3d11_2-id3d11devicecontext2-copytiles">ID3D11DeviceContext2::CopyTiles</a> operation involves copying a swizzled tiled resource to a linear buffer. This means to copy tile data from the tile region, reading tiles sequentially (in x,y,z order if the region is a box),
to the specified buffer location, deswizzling to linear memory layout as needed.
In this <b>ID3D11DeviceContext2::CopyTiles</b> call, you specify the source data with the <i>pTiledResource</i> parameter and the destination with the  <i>pBuffer</i> parameter.

## -see-also

<a href="/windows/desktop/direct3d11/d3d11-graphics-reference-resource-enums">Resource Enumerations</a>