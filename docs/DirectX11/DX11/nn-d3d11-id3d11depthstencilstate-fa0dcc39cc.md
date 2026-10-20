Source: [https://learn.microsoft.com/en-us/windows/win32/api/D3D11/nn-d3d11-id3d11depthstencilstate](<https://learn.microsoft.com/en-us/windows/win32/api/D3D11/nn-d3d11-id3d11depthstencilstate>)

# ID3D11DepthStencilState interface


## -description

The depth-stencil-state interface holds a description for depth-stencil state that you can bind to the <a href="/windows/desktop/direct3d11/d3d10-graphics-programming-guide-output-merger-stage">output-merger stage</a>.

## -inheritance

The <b>ID3D11DepthStencilState</b> interface inherits from <a href="/windows/desktop/api/d3d11/nn-d3d11-id3d11devicechild">ID3D11DeviceChild</a>. <b>ID3D11DepthStencilState</b> also has these types of members:

## -remarks

To create a depth-stencil-state object, call <a href="/windows/desktop/api/d3d11/nf-d3d11-id3d11device-createdepthstencilstate">ID3D11Device::CreateDepthStencilState</a>. To bind the depth-stencil-state object to the <a href="/windows/desktop/direct3d11/d3d10-graphics-programming-guide-output-merger-stage">output-merger stage</a>, call <a href="/windows/desktop/api/d3d11/nf-d3d11-id3d11devicecontext-omsetdepthstencilstate">ID3D11DeviceContext::OMSetDepthStencilState</a>.

## -see-also

<a href="/windows/desktop/direct3d11/d3d11-graphics-reference-d3d11-core-interfaces">Core Interfaces</a>



<a href="/windows/desktop/api/d3d11/nn-d3d11-id3d11devicechild">ID3D11DeviceChild</a>