Source: [https://learn.microsoft.com/en-us/windows/win32/direct3d11/buffer-tiling](<https://learn.microsoft.com/en-us/windows/win32/direct3d11/buffer-tiling>)

# Buffer tiling

A [Buffer](./overviews-direct3d-11-resources-buffers-1faa07e5b1.md) resource is divided into 64KB tiles, with some empty space in the last tile if the size is not a multiple of 64KB.

Structured buffers must have no constraint on the stride to be tiled. But possible performance optimizations in hardware for using [**StructuredBuffers**](/windows/desktop/direct3dhlsl/sm5-object-structuredbuffer) can be sacrificed by making them tiled in the first place.

## Related topics

<dl> <dt>

[How a tiled resource's area is tiled](./how-a-tiled-resource-s-area-is-tiled-a85cf86d83.md)
</dt> </dl>