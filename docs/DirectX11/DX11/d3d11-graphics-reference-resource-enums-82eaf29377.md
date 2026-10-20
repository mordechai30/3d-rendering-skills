Source: [https://learn.microsoft.com/en-us/windows/win32/direct3d11/d3d11-graphics-reference-resource-enums](<https://learn.microsoft.com/en-us/windows/win32/direct3d11/d3d11-graphics-reference-resource-enums>)

# Resource Enumerations (Direct3D 11 Graphics)

Enumerations are used to specify information about how resources are created and accessed during rendering.


## In this section



| Topic                                                                                                               | Description                                                                                                                                                                                   |
|---------------------------------------------------------------------------------------------------------------------|-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| [**D3D11\_BIND\_FLAG**](./ne-d3d11-d3d11_bind_flag-78d4ee3d0d.md)<br/>                                                             | Identifies how to bind a resource to the pipeline.<br/>                                                                                                                                 |
| [**D3D11\_BUFFEREX\_SRV\_FLAG**](./ne-d3d11-d3d11_bufferex_srv_flag-a6d64708d0.md)<br/>                                            | Identifies how to view a buffer resource.<br/>                                                                                                                                          |
| [**D3D11\_BUFFER\_UAV\_FLAG**](./ne-d3d11-d3d11_buffer_uav_flag-7a04d8e6a3.md)<br/>                                                | Identifies unordered-access view options for a buffer resource.<br/>                                                                                                                    |
| [**D3D11\_CHECK\_MULTISAMPLE\_QUALITY\_LEVELS\_FLAG**](./ne-d3d11_2-d3d11_check_multisample_quality_levels_flag-2d1e8e6617.md)<br/> | Identifies how to check multisample quality levels.<br/>                                                                                                                                |
| [**D3D11\_CPU\_ACCESS\_FLAG**](./ne-d3d11-d3d11_cpu_access_flag-2c51d58b52.md)<br/>                                                | Specifies the types of CPU access allowed for a resource.<br/>                                                                                                                          |
| [**D3D11\_DSV\_DIMENSION**](./ne-d3d11-d3d11_dsv_dimension-9463580cea.md)<br/>                                                     | Specifies how to access a resource used in a depth-stencil view.<br/>                                                                                                                   |
| [**D3D11\_DSV\_FLAG**](./ne-d3d11-d3d11_dsv_flag-3802a8fd3a.md)<br/>                                                               | Depth-stencil view options.<br/>                                                                                                                                                        |
| [**D3D11\_MAP**](./ne-d3d11-d3d11_map-80dcff5b4f.md)<br/>                                                                          | Identifies a resource to be accessed for reading and writing by the CPU. Applications may combine one or more of these flags.<br/>                                                      |
| [**D3D11\_MAP\_FLAG**](./ne-d3d11-d3d11_map_flag-0d847387f6.md)<br/>                                                               | Specifies how the CPU should respond when an application calls the [**ID3D11DeviceContext::Map**](./nf-d3d11-id3d11devicecontext-map-d6df2a4196.md) method on a resource that is being used by the GPU.<br/> |
| [**D3D11\_RESOURCE\_DIMENSION**](./ne-d3d11-d3d11_resource_dimension-d235061312.md)<br/>                                           | Identifies the type of resource being used.<br/>                                                                                                                                        |
| [**D3D11\_RESOURCE\_MISC\_FLAG**](./ne-d3d11-d3d11_resource_misc_flag-f85f09a16f.md)<br/>                                          | Identifies options for resources.<br/>                                                                                                                                                  |
| [**D3D11\_RTV\_DIMENSION**](./ne-d3d11-d3d11_rtv_dimension-713b849146.md)<br/>                                                     | These flags identify the type of resource that will be viewed as a render target.<br/>                                                                                                  |
| [**D3D11\_SRV\_DIMENSION**](/previous-versions/windows/desktop/legacy/ff476217(v=vs.85))<br/>                                                     | These flags identify the type of resource that will be viewed as a shader resource.<br/>                                                                                                |
| [**D3D11\_STANDARD\_MULTISAMPLE\_QUALITY\_LEVELS**](./ne-d3d11-d3d11_standard_multisample_quality_levels-e6d6b3a437.md)<br/>       | Specifies a multi-sample pattern type.<br/>                                                                                                                                             |
| [**D3D11\_TEXTURE\_LAYOUT**](./ne-d3d11_3-d3d11_texture_layout-bc934880ba.md)<br/>                                                   | Specifies texture layout options.<br/>                                                                                                                                                  |
| [**D3D11\_TILE\_COPY\_FLAG**](./ne-d3d11_2-d3d11_tile_copy_flag-546ed9795c.md)<br/>                                                 | Identifies how to copy a tile.<br/>                                                                                                                                                     |
| [**D3D11\_TILE\_MAPPING\_FLAG**](./ne-d3d11_2-d3d11_tile_mapping_flag-c17bbdd658.md)<br/>                                           | Identifies how to perform a tile-mapping operation.<br/>                                                                                                                                |
| [**D3D11\_TILE\_RANGE\_FLAG**](./ne-d3d11_2-d3d11_tile_range_flag-b965b6ab05.md)<br/>                                                | Specifies a range of tile mappings to use with [**ID3D11DeviceContext2::UpdateTiles**](./nf-d3d11_2-id3d11devicecontext2-updatetiles-5bdb764d7b.md).<br/>                                                      |
| [**D3D11\_UAV\_DIMENSION**](./ne-d3d11-d3d11_uav_dimension-1cf40336f2.md)<br/>                                                     | Unordered-access view options.<br/>                                                                                                                                                     |
| [**D3D11\_USAGE**](./ne-d3d11-d3d11_usage-8197affe09.md)<br/>                                                                      | Identifies expected resource use during rendering. The usage directly reflects whether a resource is accessible by the CPU and/or the graphics processing unit (GPU).<br/>              |



 

## Related topics

<dl> <dt>

[Resource Reference](./d3d11-graphics-reference-resource-70092c09bd.md)
</dt> </dl>