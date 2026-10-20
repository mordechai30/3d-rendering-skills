Source: [https://learn.microsoft.com/en-us/windows/win32/direct3d11/overviews-direct3d-11-resources](<https://learn.microsoft.com/en-us/windows/win32/direct3d11/overviews-direct3d-11-resources>)

# Resources

Resources provide data to the pipeline and define what is rendered during your scene. Resources can be loaded from your game media or created dynamically at run time. Typically, resources include texture data, vertex data, and shader data. Most Direct3D applications create and destroy resources extensively throughout their lifespan. This section describes aspects of Direct3D 11 resources.


## In this section



| Topic                                                                                             | Description                                                                                                                                                                                                                                        |
|---------------------------------------------------------------------------------------------------|----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| [Introduction to a Resource in Direct3D 11](./overviews-direct3d-11-resources-intro-07b5c1d0f2.md)<br/> | This topic introduces Direct3D resources such as buffers and textures.<br/>                                                                                                                                                                  |
| [Types of Resources](./overviews-direct3d-11-resources-types-0fad49d3cf.md)<br/>                        | This topic describes the types of resources from Direct3D 10, as well as new types in Direct3D 11 including structured buffers and writable textures and buffers.<br/>                                                                       |
| [Resource Limits](./overviews-direct3d-11-resources-limits-cadd01d25e.md)<br/>                          | This topic contains a list of resources that Direct3D 11 supports (specifically [feature level](./overviews-direct3d-11-devices-downlevel-intro-f595280e88.md) 11 or 9.x hardware).<br/>                                 |
| [Subresources](./overviews-direct3d-11-resources-subresources-5bd8ec8cec.md)<br/>                       | This topic describes texture subresources, or portions of a resource.<br/>                                                                                                                                                                   |
| [Buffers](./overviews-direct3d-11-resources-buffers-1faa07e5b1.md)<br/>                                 | Buffers contain data that is used for describing geometry, indexing geometry information, and shader constants. This section describes buffers that are used in Direct3D 11 and links to task-based documentation for common scenarios.<br/> |
| [Textures](./overviews-direct3d-11-resources-textures-6654061a52.md)<br/>                               | This section describes textures that are used in Direct3D 11 and links to task-based documentation for common scenarios.<br/>                                                                                                                |
| [Floating-point rules](./floating-point-rules-1858194b01.md)<br/>                                       | Direct3D 11 supports several floating-point representations. All floating-point computations operate under a defined subset of the IEEE 754 32-bit single precision floating-point rules.<br/>                                               |
| [Tiled resources](./tiled-resources-8d4a7f2d4e.md)<br/>                                                 | Tiled resources can be thought of as large logical resources that use small amounts of physical memory.<br/>                                                                                                                                 |
|[Displayable surfaces](./displayable-surfaces-447871f193.md)|The displayable surfaces feature means that buffers that are presented may have varying properties, and you may present them in any order.|

## Related topics

<dl> <dt>

[Programming Guide for Direct3D 11](./dx-graphics-overviews-1c65710e07.md)
</dt> </dl>