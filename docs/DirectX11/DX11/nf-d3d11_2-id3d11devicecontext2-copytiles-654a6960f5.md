Source: [https://learn.microsoft.com/en-us/windows/win32/api/D3D11_2/nf-d3d11_2-id3d11devicecontext2-copytiles](<https://learn.microsoft.com/en-us/windows/win32/api/D3D11_2/nf-d3d11_2-id3d11devicecontext2-copytiles>)

# ID3D11DeviceContext2::CopyTiles


## -description

Copies tiles from buffer to tiled resource or vice versa.

## -parameters

### -param pTiledResource [in]

Type: <b><a href="/windows/desktop/api/d3d11/nn-d3d11-id3d11resource">ID3D11Resource</a>*</b>

A pointer to a tiled resource.

### -param pTileRegionStartCoordinate [in]

Type: <b>const <a href="/windows/desktop/api/d3d11_2/ns-d3d11_2-d3d11_tiled_resource_coordinate">D3D11_TILED_RESOURCE_COORDINATE</a>*</b>

A pointer to a <a href="/windows/desktop/api/d3d11_2/ns-d3d11_2-d3d11_tiled_resource_coordinate">D3D11_TILED_RESOURCE_COORDINATE</a> structure that describes the starting coordinates of the tiled resource.

### -param pTileRegionSize [in]

Type: <b>const <a href="/windows/desktop/api/d3d11_2/ns-d3d11_2-d3d11_tile_region_size">D3D11_TILE_REGION_SIZE</a>*</b>

A pointer to a <a href="/windows/desktop/api/d3d11_2/ns-d3d11_2-d3d11_tile_region_size">D3D11_TILE_REGION_SIZE</a> structure that describes the size of the tiled region.

### -param pBuffer [in]

Type: <b><a href="/windows/desktop/api/d3d11/nn-d3d11-id3d11buffer">ID3D11Buffer</a>*</b>

A pointer to an <a href="/windows/desktop/api/d3d11/nn-d3d11-id3d11buffer">ID3D11Buffer</a> that represents a default, dynamic, or staging buffer.

### -param BufferStartOffsetInBytes [in]

Type: <b><a href="/windows/desktop/WinProg/windows-data-types">UINT64</a></b>

The offset in bytes into the buffer at <i>pBuffer</i> to start the operation.

### -param Flags [in]

Type: <b><a href="/windows/desktop/WinProg/windows-data-types">UINT</a></b>

A combination of <a href="/windows/desktop/api/d3d11_2/ne-d3d11_2-d3d11_tile_copy_flag">D3D11_TILE_COPY_FLAG</a>-typed values that are combined by using a bitwise OR operation and that identifies how to copy tiles.

## -remarks

<b>CopyTiles</b> drops write operations to unmapped areas and handles read operations from unmapped areas (except on <a href="/windows/desktop/api/d3d11/ne-d3d11-d3d11_tiled_resources_tier">Tier_1</a> tiled resources, where reading and writing unmapped areas is invalid).
      

If a copy operation involves writing to the same memory location multiple times because multiple locations in the destination resource are mapped to the same tile memory, the resulting write operations to multi-mapped tiles are non-deterministic and non-repeatable; that is, accesses to the tile memory happen in whatever order the hardware happens to execute the copy operation.

The tiles involved in the copy operation can't include tiles that contain packed mipmaps or results of the copy operation are undefined. To transfer data to and from mipmaps that the hardware packs into the one-or-more tiles that constitute the packed mips, you must use the standard (that is, non-tile specific) copy and update APIs (like <a href="/windows/desktop/api/d3d11_1/nf-d3d11_1-id3d11devicecontext1-copysubresourceregion1">ID3D11DeviceContext1::CopySubresourceRegion1</a> and <a href="/windows/desktop/api/d3d11_1/nf-d3d11_1-id3d11devicecontext1-updatesubresource1">ID3D11DeviceContext1::UpdateSubresource1</a>) or <a href="/windows/desktop/api/d3d11/nf-d3d11-id3d11devicecontext-generatemips">ID3D11DeviceContext::GenerateMips</a> for the whole mipmap chain.
      

The memory layout of the tiles in the non-tiled buffer resource side of the copy operation is linear in memory within 64 KB tiles, which the hardware and driver swizzle and deswizzle per tile as appropriate when they transfer to and from a tiled resource. For multisample antialiasing (MSAA) surfaces, the hardware and driver traverse each pixel's samples in sample-index order before they move to the next pixel. For tiles that are partially filled on the right side (for a surface that has a width not a multiple of tile width in pixels), the pitch and stride to move down a row is the full size in bytes of the number pixels that would fit across the tile if the tile was full. So, there can be a gap between each row of pixels in memory. Mipmaps that are smaller than a tile are not packed together in the linear layout, which might seem to be a waste of memory space, but as mentioned you can't use <b>CopyTiles</b> or <a href="/windows/desktop/api/d3d11_2/nf-d3d11_2-id3d11devicecontext2-updatetiles">ID3D11DeviceContext2::UpdateTiles</a> to copy to mipmaps that the hardware packs together. You can just use generic copy and update APIs (like <a href="/windows/desktop/api/d3d11_1/nf-d3d11_1-id3d11devicecontext1-copysubresourceregion1">ID3D11DeviceContext1::CopySubresourceRegion1</a> and <a href="/windows/desktop/api/d3d11_1/nf-d3d11_1-id3d11devicecontext1-updatesubresource1">ID3D11DeviceContext1::UpdateSubresource1</a>) to copy small mipmaps individually. Although in the case of a generic copy API (like <b>ID3D11DeviceContext1::CopySubresourceRegion1</b>), the linear memory must be the same dimension as the tiled resource; <b>ID3D11DeviceContext1::CopySubresourceRegion1</b> can't copy from a buffer resource to a Texture2D for instance.
      

For more info about tiled resources, see <a href="/windows/desktop/direct3d11/tiled-resources">Tiled resources</a>.

## -see-also

<a href="/windows/desktop/api/d3d11_2/nn-d3d11_2-id3d11devicecontext2">ID3D11DeviceContext2</a>