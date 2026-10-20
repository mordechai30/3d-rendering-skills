Source: [https://learn.microsoft.com/en-us/windows/win32/direct3d11/tiled-resource-cross-process-and-device-sharing](<https://learn.microsoft.com/en-us/windows/win32/direct3d11/tiled-resource-cross-process-and-device-sharing>)

# Tiled resource cross process and device sharing

Tile pools can be shared with other processes just like traditional resources. Tiled resources that reference tile pools can't be shared across devices and processes. But separate processes can create their own tiled resources that map to tile pools that are shared between those tiled resources.

Shared tile pools can't be resized.

## In this section



| Topic                                                                                                                   | Description                                                                     |
|-------------------------------------------------------------------------------------------------------------------------|---------------------------------------------------------------------------------|
| [Stencil formats not supported with tiled resources](./stencil-formats-not-supported-with-tiled-resources-f0a1f16563.md)<br/> | Formats that contain stencil aren't supported with tiled resources. <br/> |



 

## Related topics

<dl> <dt>

[Creating tiled resources](./creating-tiled-resources-0a11208f83.md)
</dt> </dl>