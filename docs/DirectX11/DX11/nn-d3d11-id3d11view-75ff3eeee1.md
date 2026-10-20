Source: [https://learn.microsoft.com/en-us/windows/win32/api/D3D11/nn-d3d11-id3d11view](<https://learn.microsoft.com/en-us/windows/win32/api/D3D11/nn-d3d11-id3d11view>)

# ID3D11View interface


## -description

A view interface specifies the parts of a resource the pipeline can access during rendering.

## -inheritance

The <b>ID3D11View</b> interface inherits from <a href="/windows/desktop/api/d3d11/nn-d3d11-id3d11devicechild">ID3D11DeviceChild</a>. <b>ID3D11View</b> also has these types of members:

## -remarks

A view interface is the base interface for all views. There are four types of views; a depth-stencil view, a render-target view, a shader-resource view, and an unordered-access view.

<ul>
<li>To create a render-target view, call <a href="/windows/desktop/api/d3d11/nf-d3d11-id3d11device-createrendertargetview">ID3D11Device::CreateRenderTargetView</a>.</li>
<li>To create a depth-stencil view, call <a href="/windows/desktop/api/d3d11/nf-d3d11-id3d11device-createdepthstencilview">ID3D11Device::CreateDepthStencilView</a>.</li>
<li>To create a shader-resource view, call <a href="/windows/desktop/api/d3d11/nf-d3d11-id3d11device-createshaderresourceview">ID3D11Device::CreateShaderResourceView</a>.</li>
<li>To create an unordered-access view, call <a href="/windows/desktop/api/d3d11/nf-d3d11-id3d11device-createunorderedaccessview">ID3D11Device::CreateUnorderedAccessView</a>.</li>
</ul>
All resources must be bound to the pipeline before they can be accessed.

<ul>
<li>To bind a render-target view or a depth-stencil view, call <a href="/windows/desktop/api/d3d11/nf-d3d11-id3d11devicecontext-omsetrendertargets">ID3D11DeviceContext::OMSetRenderTargets</a>.</li>
<li>To bind a shader resource, call <a href="/windows/desktop/api/d3d11/nf-d3d11-id3d11devicecontext-vssetshaderresources">ID3D11DeviceContext::VSSetShaderResources</a>.</li>
</ul>

## -see-also

<a href="/windows/desktop/api/d3d11/nn-d3d11-id3d11devicechild">ID3D11DeviceChild</a>



<a href="/windows/desktop/direct3d11/d3d11-graphics-reference-resource-interfaces">Resource Interfaces</a>