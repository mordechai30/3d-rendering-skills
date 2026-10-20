Source: [https://learn.microsoft.com/en-us/windows/win32/api/D3D11/nn-d3d11-id3d11rendertargetview](<https://learn.microsoft.com/en-us/windows/win32/api/D3D11/nn-d3d11-id3d11rendertargetview>)

# ID3D11RenderTargetView interface


## -description

A render-target-view interface identifies the render-target subresources that can be accessed during rendering.

## -inheritance

The <b>ID3D11RenderTargetView</b> interface inherits from <a href="/windows/desktop/api/d3d11/nn-d3d11-id3d11view">ID3D11View</a>. <b>ID3D11RenderTargetView</b> also has these types of members:

## -remarks

To create a render-target view, call <a href="/windows/desktop/api/d3d11/nf-d3d11-id3d11device-createrendertargetview">ID3D11Device::CreateRenderTargetView</a>. To bind a render-target view to the pipeline, call <a href="/windows/desktop/api/d3d11/nf-d3d11-id3d11devicecontext-omsetrendertargets">ID3D11DeviceContext::OMSetRenderTargets</a>.

A rendertarget is a resource that can be written by the output-merger stage at the end of a render pass. Each render-target should also have a corresponding depth-stencil view.

## -see-also

<a href="/windows/desktop/api/d3d11/nn-d3d11-id3d11view">ID3D11View</a>



<a href="/windows/desktop/direct3d11/d3d11-graphics-reference-resource-interfaces">Resource Interfaces</a>