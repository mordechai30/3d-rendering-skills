Source: [https://learn.microsoft.com/en-us/windows/win32/api/D3D11/nn-d3d11-id3d11rasterizerstate](<https://learn.microsoft.com/en-us/windows/win32/api/D3D11/nn-d3d11-id3d11rasterizerstate>)

# ID3D11RasterizerState interface


## -description

The rasterizer-state interface holds a description for rasterizer state that you can bind to the <a href="/windows/desktop/direct3d11/d3d10-graphics-programming-guide-rasterizer-stage">rasterizer stage</a>.

## -inheritance

The <b>ID3D11RasterizerState</b> interface inherits from <a href="/windows/desktop/api/d3d11/nn-d3d11-id3d11devicechild">ID3D11DeviceChild</a>. <b>ID3D11RasterizerState</b> also has these types of members:

## -remarks

To create a rasterizer-state object, call <a href="/windows/desktop/api/d3d11/nf-d3d11-id3d11device-createrasterizerstate">ID3D11Device::CreateRasterizerState</a>. To bind the rasterizer-state object to the <a href="/windows/desktop/direct3d11/d3d10-graphics-programming-guide-rasterizer-stage">rasterizer stage</a>, call <a href="/windows/desktop/api/d3d11/nf-d3d11-id3d11devicecontext-rssetstate">ID3D11DeviceContext::RSSetState</a>.

## -see-also

<a href="/windows/desktop/direct3d11/d3d11-graphics-reference-d3d11-core-interfaces">Core Interfaces</a>



<a href="/windows/desktop/api/d3d11/nn-d3d11-id3d11devicechild">ID3D11DeviceChild</a>