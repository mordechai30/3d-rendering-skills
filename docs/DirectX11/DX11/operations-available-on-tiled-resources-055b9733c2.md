Source: [https://learn.microsoft.com/en-us/windows/win32/direct3d11/operations-available-on-tiled-resources](<https://learn.microsoft.com/en-us/windows/win32/direct3d11/operations-available-on-tiled-resources>)

# Operations available on tiled resources

This section lists operations that you can perform on tiled resources.

-   void [**ID3D11DeviceContext2::UpdateTileMappings**](./nf-d3d11_2-id3d11devicecontext2-updatetilemappings-66938b64dd.md) and [**ID3D11DeviceContext2::CopyTileMappings**](./nf-d3d11_2-id3d11devicecontext2-copytilemappings-d3fe099f4a.md) operations - These operations point tile locations in a tiled resource to locations in tile pools, or to NULL, or to both. These operations can update a disjoint subset of the tile pointers.
-   Copy\*() and Update\*() operations - All the APIs that can copy data to and from a default pool surface (for example, [**ID3D11DeviceContext1::CopySubresourceRegion1**](./nf-d3d11_1-id3d11devicecontext1-copysubresourceregion1-2af7b964e3.md) and [**ID3D11DeviceContext1::UpdateSubresource1**](./nf-d3d11_1-id3d11devicecontext1-updatesubresource1-f9209fb99d.md)) work for tiled resources. Reading from unmapped tiles produces 0 and writes to unmapped tiles are dropped.
-   [**ID3D11DeviceContext2::CopyTiles**](./nf-d3d11_2-id3d11devicecontext2-copytiles-654a6960f5.md) and [**ID3D11DeviceContext2::UpdateTiles**](./nf-d3d11_2-id3d11devicecontext2-updatetiles-5bdb764d7b.md) operations - These operations exist for copying tiles at 64KB granularity to and from any tiled resource and a buffer resource in a canonical memory layout. The display driver and hardware perform any memory "swizzling" necessary for the tiled resource.
-   Direct3D pipeline bindings and view creations / bindings that would work on non-tiled resources work on tiled resources as well.

Tile controls are available on immediate or deferred contexts (just like updates to typical resources) and upon execution impact subsequent accesses to the tiles (not previously submitted operations).

## Related topics

<dl> <dt>

[Creating tiled resources](./creating-tiled-resources-0a11208f83.md)
</dt> </dl>