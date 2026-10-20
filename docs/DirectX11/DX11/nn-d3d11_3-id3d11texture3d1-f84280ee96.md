Source: [https://learn.microsoft.com/en-us/windows/win32/api/D3D11_3/nn-d3d11_3-id3d11texture3d1](<https://learn.microsoft.com/en-us/windows/win32/api/D3D11_3/nn-d3d11_3-id3d11texture3d1>)

# ID3D11Texture3D1 interface


## -description

A 3D texture interface represents texel data, which is structured memory.

## -inheritance

The <b>ID3D11Texture3D1</b> interface inherits from <a href="/windows/desktop/api/d3d11/nn-d3d11-id3d11texture3d">ID3D11Texture3D</a>. <b>ID3D11Texture3D1</b> also has these types of members:

## -remarks

To create an empty Texture3D resource, call <a href="/windows/desktop/api/d3d11_3/nf-d3d11_3-id3d11device3-createtexture3d1">ID3D11Device3::CreateTexture3D1</a>. For info about how to create a 2D texture, which is similar to creating a 3D texture, see <a href="/windows/desktop/direct3d11/overviews-direct3d-11-resources-textures-create">How to: Create a Texture</a>. 

Textures can't be bound directly to the pipeline; instead, a view must be created and bound. Using a view, texture data can be interpreted at run time within certain restrictions. To use the texture as a render-target or depth-stencil resource, call <a href="/windows/desktop/api/d3d11_3/nf-d3d11_3-id3d11device3-createrendertargetview1">ID3D11Device3::CreateRenderTargetView1</a>, and <a href="/windows/desktop/api/d3d11/nf-d3d11-id3d11device-createdepthstencilview">ID3D11Device::CreateDepthStencilView</a>, respectively. To use the texture as an input to a shader, call <a href="/windows/desktop/api/d3d11_3/nf-d3d11_3-id3d11device3-createshaderresourceview1">ID3D11Device3::CreateShaderResourceView1</a>.

## -see-also

<a href="/windows/desktop/api/d3d11/nn-d3d11-id3d11texture3d">ID3D11Texture3D</a>



<a href="/windows/desktop/direct3d11/d3d11-graphics-reference-resource-interfaces">Resource Interfaces</a>