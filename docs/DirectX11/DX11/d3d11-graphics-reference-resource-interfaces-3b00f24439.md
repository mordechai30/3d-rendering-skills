Source: [https://learn.microsoft.com/en-us/windows/win32/direct3d11/d3d11-graphics-reference-resource-interfaces](<https://learn.microsoft.com/en-us/windows/win32/direct3d11/d3d11-graphics-reference-resource-interfaces>)

# Resource Interfaces (Direct3D 11 Graphics)

There are a number of interfaces for the two basic types of resources: buffers and textures. There are also interfaces for views of resources.

An application uses a view to bind a resource to a pipeline stage. The view defines how the resource can be accessed during rendering. This section describes the view interfaces.


## In this section



| Topic                                                                       | Description                                                                                                                                                                                            |
|-----------------------------------------------------------------------------|--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| [**ID3D11Buffer**](./nn-d3d11-id3d11buffer-0e4ba9908b.md)<br/>                             | A buffer interface accesses a buffer resource, which is unstructured memory. Buffers typically store vertex or index data.<br/>                                                                  |
| [**ID3D11DepthStencilView**](./nn-d3d11-id3d11depthstencilview-6b66908b1e.md)<br/>         | A depth-stencil-view interface accesses a texture resource during depth-stencil testing.<br/>                                                                                                    |
| [**ID3D11RenderTargetView**](./nn-d3d11-id3d11rendertargetview-1a1c75b9dd.md)<br/>         | A render-target-view interface identifies the render-target subresources that can be accessed during rendering.<br/>                                                                             |
| [**ID3D11RenderTargetView1**](./nn-d3d11_3-id3d11rendertargetview1-c36b33b00e.md)<br/>       | A render-target-view interface represents the render-target subresources that can be accessed during rendering.<br/>                                                                             |
| [**ID3D11Resource**](./nn-d3d11-id3d11resource-87288ccb83.md)<br/>                         | A resource interface provides common actions on all resources.<br/>                                                                                                                              |
| [**ID3D11ShaderResourceView**](./nn-d3d11-id3d11shaderresourceview-e26d3e0c03.md)<br/>     | A shader-resource-view interface specifies the subresources a shader can access during rendering. Examples of shader resources include a constant buffer, a texture buffer, and a texture.<br/>  |
| [**ID3D11ShaderResourceView1**](./nn-d3d11_3-id3d11shaderresourceview1-ec0638238d.md)<br/>   | A shader-resource-view interface represents the subresources a shader can access during rendering. Examples of shader resources include a constant buffer, a texture buffer, and a texture.<br/> |
| [**ID3D11Texture1D**](./nn-d3d11-id3d11texture1d-8050524d5a.md)<br/>                       | A 1D texture interface accesses texel data, which is structured memory.<br/>                                                                                                                     |
| [**ID3D11Texture2D**](./nn-d3d11-id3d11texture2d-c08b027a6d.md)<br/>                       | A 2D texture interface manages texel data, which is structured memory.<br/>                                                                                                                      |
| [**ID3D11Texture2D1**](./nn-d3d11_3-id3d11texture2d1-0985e9f3a3.md)<br/>                     | A 2D texture interface represents texel data, which is structured memory.<br/>                                                                                                                   |
| [**ID3D11Texture3D**](./nn-d3d11-id3d11texture3d-16e7cb8495.md)<br/>                       | A 3D texture interface accesses texel data, which is structured memory.<br/>                                                                                                                     |
| [**ID3D11Texture3D1**](./nn-d3d11_3-id3d11texture3d1-f84280ee96.md)<br/>                     | A 3D texture interface represents texel data, which is structured memory.<br/>                                                                                                                   |
| [**ID3D11UnorderedAccessView**](./nn-d3d11-id3d11unorderedaccessview-837aae35d2.md)<br/>   | A view interface specifies the parts of a resource the pipeline can access during rendering.<br/>                                                                                                |
| [**ID3D11UnorderedAccessView1**](./nn-d3d11_3-id3d11unorderedaccessview1-6b7212236e.md)<br/> | An unordered-access-view interface represents the parts of a resource the pipeline can access during rendering.<br/>                                                                             |
| [**ID3D11View**](./nn-d3d11-id3d11view-75ff3eeee1.md)<br/>                                 | A view interface specifies the parts of a resource the pipeline can access during rendering.<br/>                                                                                                |



 

## Related topics

<dl> <dt>

[Resource Reference](./d3d11-graphics-reference-resource-70092c09bd.md)
</dt> </dl>