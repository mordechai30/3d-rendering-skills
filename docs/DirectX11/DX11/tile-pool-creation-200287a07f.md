Source: [https://learn.microsoft.com/en-us/windows/win32/direct3d11/tile-pool-creation](<https://learn.microsoft.com/en-us/windows/win32/direct3d11/tile-pool-creation>)

# Tile pool creation

A tile pool is created via the [**ID3D11Device::CreateBuffer**](./nf-d3d11-id3d11device-createbuffer-973d575f5e.md) API by passing the [**D3D11\_RESOURCE\_MISC\_TILE\_POOL**](./ne-d3d11-d3d11_resource_misc_flag-f85f09a16f.md) flag in the **MiscFlags** member of the [**D3D11\_BUFFER\_DESC**](./ns-d3d11-d3d11_buffer_desc-dbbb31b85c.md) structure that the *pDesc* parameter points to.

Applications can create one or more tile pools per Direct3D device. The total size of each tile pool is restricted to Direct3D 11's resource size limit, which is roughly 1/4 of graphics processing unit (GPU) RAM.

A tile pool is made of 64KB tiles, but the operating system (display driver) manages the entire pool as one or more allocations behind the scenes—the breakdown is not visible to applications. Tiled resources define content by pointing at tiles within a tile pool. Unmapping a tile from a tiled resource is done by pointing the tile to **NULL**. Such unmapped tiles have rules about the behavior of reads or writes. For info, see [Hazard tracking versus tile pool resources](./hazard-tracking-versus-tile-pool-resources-a6349abf26.md).

## Related topics

<dl> <dt>

[Mappings are into a tile pool](./mappings-are-into-a-tile-pool-a279a897ca.md)
</dt> </dl>