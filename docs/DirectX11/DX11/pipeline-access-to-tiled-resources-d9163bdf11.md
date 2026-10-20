Source: [https://learn.microsoft.com/en-us/windows/win32/direct3d11/pipeline-access-to-tiled-resources](<https://learn.microsoft.com/en-us/windows/win32/direct3d11/pipeline-access-to-tiled-resources>)

# Pipeline access to tiled resources

Tiled resources can be used in shader resource views (SRV), render target views (RTV), depth stencil views (DSV) and unordered access views (UAV), as well as some bind points where views aren't used, such as vertex buffer bindings. For the list of supported bindings, see [Tiled resource creation parameters](./tiled-resource-creation-parameters-4309b8e18e.md). Copy\* operations also work on tiled resources.

If multiple tile coordinates in one or more views is bound to the same memory location, reads and writes from different paths to the same memory will occur in a non-deterministic and non-repeatable order of memory accesses.

If all tiles behind a memory access footprint from a shader are mapped to unique tiles, behavior is identical on all implementations to the surface having the same memory contents in a non-tiled fashion.

This section provides more info about pipeline access to tiled resources.

## In this section



| Topic                                                                                                              | Description                                                                                                                                                               |
|--------------------------------------------------------------------------------------------------------------------|---------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| [SRV behavior with non-mapped tiles](./srv-behavior-with-non-mapped-tiles-0f1c74680d.md)<br/>                            | Behavior of shader resource view (SRV) reads that involve non-mapped tiles depends on the level of hardware support. <br/>                                          |
| [UAV behavior with non-mapped tiles](./uav-behavior-with-non-mapped-tiles-7bdbd23c90.md)<br/>                            | Behavior of unordered access view (UAV) reads and writes depends on the level of hardware support. <br/>                                                            |
| [Rasterizer behavior with non-mapped tiles](./rasterizer-behavior-with-non-mapped-tiles-91ed813725.md)<br/>              | This section describes rasterizer behavior with non-mapped tiles.<br/>                                                                                              |
| [Tile access limitations with duplicate mappings](./tile-access-limitations-with-duplicate-mappings--0ece355987.md)<br/> | This section describes tile access limitations with duplicate mappings.<br/>                                                                                        |
| [Tiled resources texture sampling features](./tiled-resources-texture-sampling-features-7dec3687b5.md)<br/>              | This section describes tiled resources texture sampling features.<br/>                                                                                              |
| [HLSL tiled resources exposure](./hlsl-tiled-resources-exposure-5c2a76f09f.md)<br/>                                      | New Microsoft High Level Shader Language (HLSL) syntax is required to support tiled resources in [Shader Model 5](/windows/desktop/direct3dhlsl/d3d11-graphics-reference-sm5). <br/> |



 

## Related topics

<dl> <dt>

[Tiled resources](./tiled-resources-8d4a7f2d4e.md)
</dt> </dl>