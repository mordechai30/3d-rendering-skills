Source: [https://learn.microsoft.com/en-us/windows/win32/api/D3D11/nn-d3d11-id3d11depthstencilview](<https://learn.microsoft.com/en-us/windows/win32/api/D3D11/nn-d3d11-id3d11depthstencilview>)

# ID3D11DepthStencilView interface


## -description

A depth-stencil-view interface accesses a texture resource during depth-stencil testing.

## -inheritance

The <b>ID3D11DepthStencilView</b> interface inherits from <a href="/windows/desktop/api/d3d11/nn-d3d11-id3d11view">ID3D11View</a>. <b>ID3D11DepthStencilView</b> also has these types of members:

## -remarks

To create a depth-stencil view, call <a href="/windows/desktop/api/d3d11/nf-d3d11-id3d11device-createdepthstencilview">ID3D11Device::CreateDepthStencilView</a>.

To bind a depth-stencil view to the pipeline, call <a href="/windows/desktop/api/d3d11/nf-d3d11-id3d11devicecontext-omsetrendertargets">ID3D11DeviceContext::OMSetRenderTargets</a>.

## -see-also

<a href="/windows/desktop/api/d3d11/nn-d3d11-id3d11view">ID3D11View</a>



<a href="/windows/desktop/direct3d11/d3d11-graphics-reference-resource-interfaces">Resource Interfaces</a>