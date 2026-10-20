Source: [https://learn.microsoft.com/en-us/windows/win32/direct3d11/volume-tiled-resources](<https://learn.microsoft.com/en-us/windows/win32/direct3d11/volume-tiled-resources>)

# Volume Tiled Resources

Volume (3D) textures can be used as tiled resources, noting that tile resolution is three-dimensional.

-   [Overview](#overview)
-   [D3D11.3 Tiled Resource APIs](#d3d113-tiled-resource-apis)
-   [Related topics](#related-topics)

## Overview

Tiled resources decouple a D3D Resource object from its backing memory (resources in the past had a 1:1 relationship with their backing memory). This allows for a variety of interesting scenarios such as streaming in texture data and reusing or reducing memory usage

2D texture tiled resources are supported in D3D11.2. D3D12 and D3D11.3 add support for 3D tiled textures.

The typical resource dimensions used in tiling are 4 x 4 tiles for 2D textures, and 4 x 4 x 4 tiles for 3D textures.



| Bits/pixel (1 sample/pixel)                            | Tile dimensions (pixels, w x h x d)                                    |
|-----------------------------|-------------------------------------|
| 8                           | 64x32x32                            |
| 16                          | 32x32x32                            |
| 32                          | 32x32x16                            |
| 64                          | 32x16x16                            |
| 128                         | 16x16x16                            |
| BC 1,4                      | 128x64x16                           |
| BC 2,3,5,6,7                | 64x64x16                            |



 

Note the following formats are not supported with tiled resources: 96bpp formats, video formats, R1\_UNORM, R8G8\_B8G8\_UNORM, R8R8\_G8B8\_UNORM.

In the diagrams below dark gray represents NULL tiles.

-   [Texture 3D Tiled Resource default mapping (most detailed mip)](#texture-3d-tiled-resource-default-mapping-most-detailed-mip)
-   [Texture 3D Tiled Resource default mapping (second most detailed mip)](#texture-3d-tiled-resource-default-mapping-second-most-detailed-mip)
-   [Texture 3D Tiled Resource (most detailed mip)](#texture-3d-tiled-resource-most-detailed-mip)
-   [Texture 3D Tiled Resource (second most detailed mip)](#texture-3d-tiled-resource-second-most-detailed-mip)
-   [Texture 3D Tiled Resource (Single Tile)](#texture-3d-tiled-resource-single-tile)
-   [Texture 3D Tiled Resource (Uniform Box)](#texture-3d-tiled-resource-uniform-box)

### Texture 3D Tiled Resource default mapping (most detailed mip)

![default mapping of the most detailed mip](<volume-tiled-resources/94ad561187b7d5a0a4879b2a.png>)

### Texture 3D Tiled Resource default mapping (second most detailed mip)

![default mapping of the second most detailed mip](<volume-tiled-resources/605197d1b07291d8ceabe497.png>)

### Texture 3D Tiled Resource (most detailed mip)

The following code sets up a 3D tiled resource at the most detailed mip.

``` syntax
D3D11_TILED_RESOURCE_COORDINATE trCoord;
trCoord.X = 1;
trCoord.Y = 0;
trCoord.Z = 0;
trCoord.Subresource = 0;

D3D11_TILE_REGION_SIZE trSize;
trSize.bUseBox = false;
trSize.NumTiles = 63;
```

![most detailed mapping of a 3d tiled resource](<volume-tiled-resources/fd1dd856df3a62cbaf63b573.png>)

### Texture 3D Tiled Resource (second most detailed mip)

The following code sets up a 3D tiled resource, and the second most detailed mip:

``` syntax
D3D11_TILED_RESOURCE_COORDINATE trCoord;
trCoord.X = 1;
trCoord.Y = 0;
trCoord.Z = 0;
trCoord.Subresource = 1;

D3D11_TILE_REGION_SIZE trSize;
trSize.bUseBox = false;
trSize.NumTiles = 6;
```

![second most detailed mapping of a 3d tiled resource](<volume-tiled-resources/8b74cbe5520123111c07fb27.png>)

### Texture 3D Tiled Resource (Single Tile)

The following code sets up a Single Tile resource:

``` syntax
D3D11_TILED_RESOURCE_COORDINATE trCoord;
trCoord.X = 1;
trCoord.Y = 1;
trCoord.Z = 1;
trCoord.Subresource = 0;

D3D11_TILE_REGION_SIZE trSize;
trSize.bUseBox = true;
trSize.NumTiles = 27;
trSize.Width = 3;
trSize.Height = 3;
trSize.Depth = 3;
```

![a single tile](<volume-tiled-resources/cddbc1c105f88d31be777d2b.png>)

### Texture 3D Tiled Resource (Uniform Box)

The following code sets up a Uniform Box tiled resource (note the statement `trSize.bUseBox = true;) :`

``` syntax
D3D11_TILED_RESOURCE_COORDINATE trCoord;
trCoord.X = 0;
trCoord.Y = 1;
trCoord.Z = 0;
trCoord.Subresource = 0;

D3D11_TILE_REGION_SIZE trSize;
trSize.bUseBox = true;
trSize.NumTiles = 27;
trSize.Width = 3;
trSize.Height = 3;
trSize.Depth = 3;
```

![a uniform box](<volume-tiled-resources/1ef237080dcf027eb20d4307.png>)

## D3D11.3 Tiled Resource APIs

The same API calls are used for both 2D and 3D tiled resources:

Enums

-   [**D3D11\_TILED\_RESOURCES\_TIER**](./ne-d3d11-d3d11_tiled_resources_tier-5ee336d92f.md) : determines the level of tiled resource support.
-   [**D3D11\_FORMAT\_SUPPORT2**](./ne-d3d11-d3d11_format_support2-4c684fd980.md) : used to test for tiled resource support.
-   [**D3D11\_CHECK\_MULTISAMPLE\_QUALITY\_LEVELS\_FLAG**](./ne-d3d11_2-d3d11_check_multisample_quality_levels_flag-2d1e8e6617.md) : determines tiled resource support in a multi-sampling resource.
-   [**D3D11\_TILE\_COPY\_FLAGS**](./ne-d3d11_2-d3d11_tile_copy_flag-546ed9795c.md) : holds flags for copying to and from swizzled tiled resources and linear buffers.

Structures

-   [**D3D11\_TILED\_RESOURCE\_COORDINATE**](./ns-d3d11_2-d3d11_tiled_resource_coordinate-8fc7ae86bf.md) : holds the x, y, and z co-ordinate, and subresource reference. Note there is a helper class: CD3D11\_TILED\_RESOURCE\_COORDINATE.
-   [**D3D11\_TILE\_REGION\_SIZE**](./ns-d3d11_2-d3d11_tile_region_size-dc7f44a3b2.md) : specifies the size, and number of tiles, of the tiled region.
-   [**D3D11\_TILE\_SHAPE**](./ns-d3d11_2-d3d11_tile_shape-26c65975dd.md) : the tile shape as a width, height and depth in texels.
-   [**D3D11\_FEATURE\_DATA\_D3D11\_OPTIONS1**](./ns-d3d11-d3d11_feature_data_d3d11_options1-7d38ff7774.md): holds the supported tile resource tier level.

Methods

-   [**ID3D11Device::CheckFeatureSupport**](./nf-d3d11-id3d11device-checkfeaturesupport-ec5826ac8e.md) : used to determine what features, and at what tier, are supported by the current hardware.
-   [**ID3D11DeviceContext2::CopyTiles**](./nf-d3d11_2-id3d11devicecontext2-copytiles-654a6960f5.md) : copies tiles from buffer to tiled resource or vice versa.
-   [**ID3D11DeviceContext2::UpdateTileMappings**](./nf-d3d11_2-id3d11devicecontext2-updatetilemappings-66938b64dd.md) : updates mappings of tile locations in tiled resources to memory locations in a tile pool.
-   [**ID3D11DeviceContext2::CopyTileMappings**](./nf-d3d11_2-id3d11devicecontext2-copytilemappings-d3fe099f4a.md) : copies mappings from a source tiled resource to a destination tiled resource.
-   [**ID3D11DeviceContext2::GetResourceTiling**](./nf-d3d11_2-id3d11device2-getresourcetiling-de5f1c761e.md) : gets info about how a tiled resource is broken into tiles.

## Related topics

<dl> <dt>

[Direct3D 11.3 Features](./direct3d-11-3-features-87cd0e6b8b.md)
</dt> </dl>