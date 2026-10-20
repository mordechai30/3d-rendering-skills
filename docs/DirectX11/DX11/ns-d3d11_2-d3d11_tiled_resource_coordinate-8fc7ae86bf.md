Source: [https://learn.microsoft.com/en-us/windows/win32/api/D3D11_2/ns-d3d11_2-d3d11_tiled_resource_coordinate](<https://learn.microsoft.com/en-us/windows/win32/api/D3D11_2/ns-d3d11_2-d3d11_tiled_resource_coordinate>)

# D3D11_TILED_RESOURCE_COORDINATE structure


## -description

Describes the coordinates of a tiled resource.

## -struct-fields

### -field X

Type: <b><a href="/windows/desktop/WinProg/windows-data-types">UINT</a></b>

The x position of a tiled resource. Used for buffer and 1D, 2D, and 3D textures.

### -field Y

Type: <b><a href="/windows/desktop/WinProg/windows-data-types">UINT</a></b>

The y position of a tiled resource. Used for 2D and 3D textures.

### -field Z

Type: <b><a href="/windows/desktop/WinProg/windows-data-types">UINT</a></b>

The z position of a tiled resource. Used for 3D textures.

### -field Subresource

Type: <b><a href="/windows/desktop/WinProg/windows-data-types">UINT</a></b>

A subresource index value into mipmaps and arrays. Used for 1D, 2D, and 3D textures. 

For mipmaps that use nonstandard tiling, or are packed, or both use nonstandard tiling and are packed, any subresource value that indicates any of the packed mipmaps all refer to the same tile.

## -see-also

<a href="/windows/desktop/direct3d11/d3d11-graphics-reference-resource-structures">Resource Structures</a>