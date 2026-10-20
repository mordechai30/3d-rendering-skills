Source: [https://learn.microsoft.com/en-us/windows/win32/direct3d11/direct3d-11-3-features](<https://learn.microsoft.com/en-us/windows/win32/direct3d11/direct3d-11-3-features>)

# Direct3D 11.3 Features

The following sections describe the functionality has been added in Direct3D 11.3. These features are also available in Direct3D 12.


## In this section



| Topic                                                                                               | Description                                                                                                                                                                                                                                                                                                                                                                                  |
|-----------------------------------------------------------------------------------------------------|----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| [Conservative Rasterization](./conservative-rasterization-6780a9e230.md)<br/>                             | Conservative rasterization adds some certainty to pixel rendering, which is helpful in particular to collision detection algorithms.<br/>                                                                                                                                                                                                                                              |
| [Default Texture Mapping](./default-texture-mapping-e1ce88c693.md)<br/>                                   | The use of default texture mapping reduces copying and memory usage while sharing image data between the GPU and the CPU. However, it should only be used in specific situations. The standard swizzle layout avoids copying or swizzling data in multiple layouts.<br/>                                                                                                               |
| [Rasterizer Order Views](./rasterizer-order-views-e7182b94cf.md)<br/>                                     | Rasterizer ordered views (ROVs) allow pixel shader code to mark UAV bindings with a declaration that alters the normal requirements for the order of graphics pipeline results for UAVs. This enables Order Independent Transparency (OIT) algorithms to work, which give much better rendering results when multiple transparent objects are in line with each other in a view. <br/> |
| [Shader Specified Stencil Reference Value](./shader-specified-stencil-reference-value-4d0299e892.md)<br/> | Enabling pixel shaders to output the Stencil Reference Value, rather than using the API-specified one, enables a very fine granular control over stencil operations.<br/>                                                                                                                                                                                                              |
| [Typed Unordered Access View Loads](./typed-unordered-access-view-loads-f96b9fb948.md)<br/>               | Unordered Access View (UAV) Typed Load is the ability for a shader to read from a UAV with a specific DXGI\_FORMAT.<br/>                                                                                                                                                                                                                                                               |
| [Unified Memory Architecture](./unified-memory-architecture-6fa868f4e7.md)<br/>                           | Querying for whether Unified Memory Architecture (UMA) is supported can help determine how to handle some resources.<br/>                                                                                                                                                                                                                                                              |
| [Volume Tiled Resources](./volume-tiled-resources-f11744b36d.md)<br/>                                     | Volume (3D) textures can be used as tiled resources, noting that tile resolution is three-dimensional.<br/>                                                                                                                                                                                                                                                                            |



 

## Related topics

<dl> <dt>

[What's new in Direct3D 11](./dx-graphics-overviews-introduction-99897347f0.md)
</dt> </dl>