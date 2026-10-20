Source: [https://learn.microsoft.com/en-us/windows/win32/api/D3D11_3/nn-d3d11_3-id3d11shaderresourceview1](<https://learn.microsoft.com/en-us/windows/win32/api/D3D11_3/nn-d3d11_3-id3d11shaderresourceview1>)

# ID3D11ShaderResourceView1 interface


## -description

A shader-resource-view interface represents the subresources a shader can access during rendering. Examples of shader resources include a constant buffer, a texture buffer, and a texture.

## -inheritance

The <b>ID3D11ShaderResourceView1</b> interface inherits from <a href="/windows/desktop/api/d3d11/nn-d3d11-id3d11shaderresourceview">ID3D11ShaderResourceView</a>. <b>ID3D11ShaderResourceView1</b> also has these types of members:

## -remarks

To create a shader-resource view, call <a href="/windows/desktop/api/d3d11_3/nf-d3d11_3-id3d11device3-createshaderresourceview1">ID3D11Device3::CreateShaderResourceView1</a>.

A shader-resource view is required when binding a resource to a shader stage; the binding occurs by calling <a href="/windows/desktop/api/d3d11/nf-d3d11-id3d11devicecontext-gssetshaderresources">ID3D11DeviceContext::GSSetShaderResources</a>, <a href="/windows/desktop/api/d3d11/nf-d3d11-id3d11devicecontext-vssetshaderresources">ID3D11DeviceContext::VSSetShaderResources</a> or <a href="/windows/desktop/api/d3d11/nf-d3d11-id3d11devicecontext-pssetshaderresources">ID3D11DeviceContext::PSSetShaderResources</a>.

## -see-also

<a href="/windows/desktop/api/d3d11/nn-d3d11-id3d11shaderresourceview">ID3D11ShaderResourceView</a>



<a href="/windows/desktop/direct3d11/d3d11-graphics-reference-resource-interfaces">Resource Interfaces</a>