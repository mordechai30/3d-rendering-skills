Source: [https://learn.microsoft.com/en-us/windows/win32/direct3d11/d3d11-graphics-reference-resource-structures](<https://learn.microsoft.com/en-us/windows/win32/direct3d11/d3d11-graphics-reference-resource-structures>)

# Resource Structures (Direct3D 11 Graphics)

Structures are used to create and use resources.


## In this section



| Topic                                                                                         | Description                                                                                                       |
|-----------------------------------------------------------------------------------------------|-------------------------------------------------------------------------------------------------------------------|
| [**D3D11\_BUFFER\_DESC**](./ns-d3d11-d3d11_buffer_desc-dbbb31b85c.md)<br/>                                   | Describes a buffer resource.<br/>                                                                           |
| [**D3D11\_BUFFER\_RTV**](./ns-d3d11-d3d11_buffer_rtv-5a77852aec.md)<br/>                                     | Specifies the elements in a buffer resource to use in a render-target view.<br/>                            |
| [**D3D11\_BUFFER\_SRV**](./ns-d3d11-d3d11_buffer_srv-95df7e9ca6.md)<br/>                                     | Specifies the elements in a buffer resource to use in a shader-resource view.<br/>                          |
| [**D3D11\_BUFFER\_UAV**](./ns-d3d11-d3d11_buffer_uav-b169f2d44d.md)<br/>                                     | Describes the elements in a buffer to use in a unordered-access view.<br/>                                  |
| [**D3D11\_BUFFEREX\_SRV**](./ns-d3d11-d3d11_bufferex_srv-d033186fe8.md)<br/>                                 | Describes the elements in a raw buffer resource to use in a shader-resource view.<br/>                      |
| [**D3D11\_DEPTH\_STENCIL\_VIEW\_DESC**](./ns-d3d11-d3d11_depth_stencil_view_desc-0538facd4a.md)<br/>         | Specifies the subresources of a texture that are accessible from a depth-stencil view.<br/>                 |
| [**D3D11\_MAPPED\_SUBRESOURCE**](./ns-d3d11-d3d11_mapped_subresource-5dbbf0bcb8.md)<br/>                     | Provides access to subresource data.<br/>                                                                   |
| [**D3D11\_PACKED\_MIP\_DESC**](./ns-d3d11_2-d3d11_packed_mip_desc-46c960c322.md)<br/>                          | Describes the tile structure of a tiled resource with mipmaps. <br/>                                        |
| [**D3D11\_RENDER\_TARGET\_VIEW\_DESC**](./ns-d3d11-d3d11_render_target_view_desc-24a3909832.md)<br/>         | Specifies the subresources from a resource that are accessible using a render-target view.<br/>             |
| [**D3D11\_RENDER\_TARGET\_VIEW\_DESC1**](./ns-d3d11_3-cd3d11_render_target_view_desc1-df51f453ce.md)<br/>       | Describes the subresources from a resource that are accessible using a render-target view.<br/>             |
| [**D3D11\_SHADER\_RESOURCE\_VIEW\_DESC**](./ns-d3d11-d3d11_shader_resource_view_desc-a2ad888d5c.md)<br/>     | Describes a shader-resource view.<br/>                                                                      |
| [**D3D11\_SHADER\_RESOURCE\_VIEW\_DESC1**](./ns-d3d11_3-cd3d11_shader_resource_view_desc1-4a099a6420.md)<br/>   | Describes a shader-resource view.<br/>                                                                      |
| [**D3D11\_SUBRESOURCE\_DATA**](./ns-d3d11-d3d11_subresource_data-0227c25259.md)<br/>                         | Specifies data for initializing a subresource.<br/>                                                         |
| [**D3D11\_SUBRESOURCE\_TILING**](./ns-d3d11_2-d3d11_subresource_tiling-0a128c76e2.md)<br/>                     | Describes a tiled subresource volume.<br/>                                                                  |
| [**D3D11\_TEX1D\_ARRAY\_DSV**](./ns-d3d11-d3d11_tex1d_array_dsv-d535dfc2c1.md)<br/>                          | Specifies the subresources from an array of 1D textures to use in a depth-stencil view.<br/>                |
| [**D3D11\_TEX1D\_ARRAY\_RTV**](./ns-d3d11-d3d11_tex1d_array_rtv-0c2b8b2c0a.md)<br/>                          | Specifies the subresources from an array of 1D textures to use in a render-target view.<br/>                |
| [**D3D11\_TEX1D\_ARRAY\_SRV**](./ns-d3d11-d3d11_tex1d_array_srv-38390a6eb7.md)<br/>                          | Specifies the subresources from an array of 1D textures to use in a shader-resource view.<br/>              |
| [**D3D11\_TEX1D\_ARRAY\_UAV**](./ns-d3d11-d3d11_tex1d_array_uav-4c54f47ab5.md)<br/>                          | Describes an array of unordered-access 1D texture resources.<br/>                                           |
| [**D3D11\_TEX1D\_DSV**](./ns-d3d11-d3d11_tex1d_dsv-bc18046252.md)<br/>                                       | Specifies the subresource from a 1D texture that is accessible to a depth-stencil view.<br/>                |
| [**D3D11\_TEX1D\_RTV**](./ns-d3d11-d3d11_tex1d_rtv-6ca47edcb0.md)<br/>                                       | Specifies the subresource from a 1D texture to use in a render-target view.<br/>                            |
| [**D3D11\_TEX1D\_SRV**](./ns-d3d11-d3d11_tex1d_srv-088e577773.md)<br/>                                       | Specifies the subresource from a 1D texture to use in a shader-resource view.<br/>                          |
| [**D3D11\_TEX1D\_UAV**](./ns-d3d11-d3d11_tex1d_uav-0767ceb244.md)<br/>                                       | Describes a unordered-access 1D texture resource.<br/>                                                      |
| [**D3D11\_TEX2D\_ARRAY\_DSV**](./ns-d3d11-d3d11_tex2d_array_dsv-9fbeb6223b.md)<br/>                          | Specifies the subresources from an array 2D textures that are accessible to a depth-stencil view.<br/>      |
| [**D3D11\_TEX2D\_ARRAY\_RTV**](./ns-d3d11-d3d11_tex2d_array_rtv-46bc8fee81.md)<br/>                          | Specifies the subresources from an array of 2D textures to use in a render-target view.<br/>                |
| [**D3D11\_TEX2D\_ARRAY\_RTV1**](./ns-d3d11_3-d3d11_tex2d_array_rtv1-6c629af128.md)<br/>                        | Describes the subresources from an array of 2D textures to use in a render-target view.<br/>                |
| [**D3D11\_TEX2D\_ARRAY\_SRV**](./ns-d3d11-d3d11_tex2d_array_srv-20a5570b09.md)<br/>                          | Specifies the subresources from an array of 2D textures to use in a shader-resource view.<br/>              |
| [**D3D11\_TEX2D\_ARRAY\_SRV1**](./ns-d3d11_3-d3d11_tex2d_array_srv1-4b5aac7689.md)<br/>                        | Describes the subresources from an array of 2D textures to use in a shader-resource view.<br/>              |
| [**D3D11\_TEX2D\_ARRAY\_UAV**](./ns-d3d11-d3d11_tex2d_array_uav-7c23da8d0d.md)<br/>                          | Describes an array of unordered-access 2D texture resources.<br/>                                           |
| [**D3D11\_TEX2D\_ARRAY\_UAV1**](./ns-d3d11_3-d3d11_tex2d_array_uav1-8b15467ca6.md)<br/>                        | Describes an array of unordered-access 2D texture resources.<br/>                                           |
| [**D3D11\_TEX2D\_DSV**](./ns-d3d11-d3d11_tex2d_dsv-bfa9bb1080.md)<br/>                                       | Specifies the subresource from a 2D texture that is accessible to a depth-stencil view.<br/>                |
| [**D3D11\_TEX2D\_RTV**](./ns-d3d11-d3d11_tex2d_rtv-0b0f761a15.md)<br/>                                       | Specifies the subresource from a 2D texture to use in a render-target view.<br/>                            |
| [**D3D11\_TEX2D\_RTV1**](./ns-d3d11_3-d3d11_tex2d_rtv1-89d64a7404.md)<br/>                                     | Describes the subresource from a 2D texture to use in a render-target view.<br/>                            |
| [**D3D11\_TEX2D\_SRV**](./ns-d3d11-d3d11_tex2d_srv-f3003d0141.md)<br/>                                       | Specifies the subresource from a 2D texture to use in a shader-resource view.<br/>                          |
| [**D3D11\_TEX2D\_SRV1**](./ns-d3d11_3-d3d11_tex2d_srv1-ec1400a262.md)<br/>                                     | Describes the subresource from a 2D texture to use in a shader-resource view.<br/>                          |
| [**D3D11\_TEX2D\_UAV**](./ns-d3d11-d3d11_tex2d_uav-49bb11ecb7.md)<br/>                                       | Describes a unordered-access 2D texture resource.<br/>                                                      |
| [**D3D11\_TEX2D\_UAV1**](./ns-d3d11_3-d3d11_tex2d_uav1-da5151de38.md)<br/>                                     | Describes a unordered-access 2D texture resource.<br/>                                                      |
| [**D3D11\_TEX2DMS\_ARRAY\_DSV**](./ns-d3d11-d3d11_tex2dms_array_dsv-f57a1e3ffa.md)<br/>                      | Specifies the subresources from an array of multisampled 2D textures for a depth-stencil view.<br/>         |
| [**D3D11\_TEX2DMS\_ARRAY\_RTV**](./ns-d3d11-d3d11_tex2dms_array_rtv-3b3be6fb08.md)<br/>                      | Specifies the subresources from a an array of multisampled 2D textures to use in a render-target view.<br/> |
| [**D3D11\_TEX2DMS\_ARRAY\_SRV**](./ns-d3d11-d3d11_tex2dms_array_srv-e87173cc22.md)<br/>                      | Specifies the subresources from an array of multisampled 2D textures to use in a shader-resource view.<br/> |
| [**D3D11\_TEX2DMS\_DSV**](./ns-d3d11-d3d11_tex2dms_dsv-430194723a.md)<br/>                                   | Specifies the subresource from a multisampled 2D texture that is accessible to a depth-stencil view.<br/>   |
| [**D3D11\_TEX2DMS\_RTV**](./ns-d3d11-d3d11_tex2dms_rtv-86c14965e9.md)<br/>                                   | Specifies the subresource from a multisampled 2D texture to use in a render-target view.<br/>               |
| [**D3D11\_TEX2DMS\_SRV**](./ns-d3d11-d3d11_tex2dms_srv-83b2d8de23.md)<br/>                                   | Specifies the subresources from a multisampled 2D texture to use in a shader-resource view.<br/>            |
| [**D3D11\_TEX3D\_RTV**](./ns-d3d11-d3d11_tex3d_rtv-c4237dc17f.md)<br/>                                       | Specifies the subresources from a 3D texture to use in a render-target view.<br/>                           |
| [**D3D11\_TEX3D\_SRV**](./ns-d3d11-d3d11_tex3d_srv-a8543ff1ac.md)<br/>                                       | Specifies the subresources from a 3D texture to use in a shader-resource view.<br/>                         |
| [**D3D11\_TEX3D\_UAV**](./ns-d3d11-d3d11_tex3d_uav-8ca36ef67e.md)<br/>                                       | Describes a unordered-access 3D texture resource.<br/>                                                      |
| [**D3D11\_TEXCUBE\_ARRAY\_SRV**](./ns-d3d11-d3d11_texcube_array_srv-a797605a81.md)<br/>                      | Specifies the subresources from an array of cube textures to use in a shader-resource view.<br/>            |
| [**D3D11\_TEXCUBE\_SRV**](./ns-d3d11-d3d11_texcube_srv-0da46965da.md)<br/>                                   | Specifies the subresource from a cube texture to use in a shader-resource view.<br/>                        |
| [**D3D11\_TEXTURE1D\_DESC**](./ns-d3d11-d3d11_texture1d_desc-c3d05a0dcc.md)<br/>                             | Describes a 1D texture.<br/>                                                                                |
| [**D3D11\_TEXTURE2D\_DESC**](./ns-d3d11-d3d11_texture2d_desc-f26127b311.md)<br/>                             | Describes a 2D texture.<br/>                                                                                |
| [**D3D11\_TEXTURE2D\_DESC1**](./ns-d3d11_3-cd3d11_texture2d_desc1-162868aa2a.md)<br/>                           | Describes a 2D texture.<br/>                                                                                |
| [**D3D11\_TEXTURE3D\_DESC**](./ns-d3d11-d3d11_texture3d_desc-c3dd187a6e.md)<br/>                             | Describes a 3D texture.<br/>                                                                                |
| [**D3D11\_TEXTURE3D\_DESC1**](./ns-d3d11_3-cd3d11_texture3d_desc1-7b794bedb9.md)<br/>                           | Describes a 3D texture.<br/>                                                                                |
| [**D3D11\_TILE\_REGION\_SIZE**](./ns-d3d11_2-d3d11_tile_region_size-dc7f44a3b2.md)<br/>                        | Describes the size of a tiled region.<br/>                                                                  |
| [**D3D11\_TILED\_RESOURCE\_COORDINATE**](./ns-d3d11_2-d3d11_tiled_resource_coordinate-8fc7ae86bf.md)<br/>      | Describes the coordinates of a tiled resource.<br/>                                                         |
| [**D3D11\_TILE\_SHAPE**](./ns-d3d11_2-d3d11_tile_shape-26c65975dd.md)<br/>                                     | Describes the shape of a tile by specifying its dimensions.<br/>                                            |
| [**D3D11\_UNORDERED\_ACCESS\_VIEW\_DESC**](./ns-d3d11-d3d11_unordered_access_view_desc-8dacba4e65.md)<br/>   | Specifies the subresources from a resource that are accessible using an unordered-access view.<br/>         |
| [**D3D11\_UNORDERED\_ACCESS\_VIEW\_DESC1**](./ns-d3d11_3-cd3d11_unordered_access_view_desc1-e59b74a0a7.md)<br/> | Describes the subresources from a resource that are accessible using an unordered-access view.<br/>         |



 

## Related topics

<dl> <dt>

[Resource Reference](./d3d11-graphics-reference-resource-70092c09bd.md)
</dt> </dl>