Source: [https://learn.microsoft.com/en-us/windows/win32/api/D3D11_2/nf-d3d11_2-id3d11device2-getresourcetiling](<https://learn.microsoft.com/en-us/windows/win32/api/D3D11_2/nf-d3d11_2-id3d11device2-getresourcetiling>)

# ID3D11Device2::GetResourceTiling


## -description

Gets info about how a tiled resource is broken into tiles.

## -parameters

### -param pTiledResource [in]

Type: <b><a href="/windows/desktop/api/d3d11/nn-d3d11-id3d11resource">ID3D11Resource</a>*</b>

A pointer to the tiled resource to get info about.

### -param pNumTilesForEntireResource [out, optional]

Type: <b><a href="/windows/desktop/WinProg/windows-data-types">UINT</a>*</b>

A pointer to a variable that receives the number of tiles needed to store the entire tiled resource.

### -param pPackedMipDesc [out, optional]

Type: <b><a href="/windows/desktop/api/d3d11_2/ns-d3d11_2-d3d11_packed_mip_desc">D3D11_PACKED_MIP_DESC</a>*</b>

A pointer to a <a href="/windows/desktop/api/d3d11_2/ns-d3d11_2-d3d11_packed_mip_desc">D3D11_PACKED_MIP_DESC</a> structure that <b>GetResourceTiling</b> fills with info about how the tiled resource's mipmaps are packed.

### -param pStandardTileShapeForNonPackedMips [out, optional]

Type: <b><a href="/windows/desktop/api/d3d11_2/ns-d3d11_2-d3d11_tile_shape">D3D11_TILE_SHAPE</a>*</b>

A pointer to a <a href="/windows/desktop/api/d3d11_2/ns-d3d11_2-d3d11_tile_shape">D3D11_TILE_SHAPE</a> structure that <b>GetResourceTiling</b> fills with info about the tile shape. This is info about how pixels fit in the tiles, independent of tiled resource's dimensions,
            not including packed mipmaps.  If the entire tiled resource is packed, this parameter is meaningless because the tiled resource has no defined layout
            for packed mipmaps.
            In this situation, <b>GetResourceTiling</b> sets the members of <b>D3D11_TILE_SHAPE</b> to zeros.

### -param pNumSubresourceTilings [in, out, optional]

Type: <b><a href="/windows/desktop/WinProg/windows-data-types">UINT</a>*</b>

A pointer to a variable that contains the number of tiles in the subresource. On input, this is the number of subresources to query tilings for; on output, this is the number that was actually retrieved at <i>pSubresourceTilingsForNonPackedMips</i> (clamped to what's available).

### -param FirstSubresourceTilingToGet [in]

Type: <b><a href="/windows/desktop/WinProg/windows-data-types">UINT</a></b>

The number of the first subresource tile to get. <b>GetResourceTiling</b> ignores this parameter if the number that <i>pNumSubresourceTilings</i> points to is 0.

### -param pSubresourceTilingsForNonPackedMips [out]

Type: <b><a href="/windows/desktop/api/d3d11_2/ns-d3d11_2-d3d11_subresource_tiling">D3D11_SUBRESOURCE_TILING</a>*</b>

A pointer to a <a href="/windows/desktop/api/d3d11_2/ns-d3d11_2-d3d11_subresource_tiling">D3D11_SUBRESOURCE_TILING</a> structure that <b>GetResourceTiling</b> fills with info about subresource tiles.
          

If subresource tiles are part of packed mipmaps, <b>GetResourceTiling</b> sets the members of <a href="/windows/desktop/api/d3d11_2/ns-d3d11_2-d3d11_subresource_tiling">D3D11_SUBRESOURCE_TILING</a> to zeros, except the <b>StartTileIndexInOverallResource</b> member, which <b>GetResourceTiling</b> sets to <b>D3D11_PACKED_TILE</b> (0xffffffff). The <b>D3D11_PACKED_TILE</b> constant indicates that the whole
            <b>D3D11_SUBRESOURCE_TILING</b> structure is meaningless for this situation, and the info that the <i>pPackedMipDesc</i> parameter points to applies.

## -remarks

For more info about tiled resources, see <a href="/windows/desktop/direct3d11/tiled-resources">Tiled resources</a>.

## -see-also

<a href="/windows/desktop/api/d3d11_2/nn-d3d11_2-id3d11device2">ID3D11Device2</a>