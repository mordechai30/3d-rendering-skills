Source: [https://learn.microsoft.com/en-us/windows/win32/api/D3D11_1/nn-d3d11_1-id3d11rasterizerstate1](<https://learn.microsoft.com/en-us/windows/win32/api/D3D11_1/nn-d3d11_1-id3d11rasterizerstate1>)

# ID3D11RasterizerState1 interface


## -description

The rasterizer-state interface holds a description for rasterizer state that you can bind to the <a href="/windows/desktop/direct3d11/d3d10-graphics-programming-guide-rasterizer-stage">rasterizer stage</a>. This rasterizer-state interface supports forced sample count.

## -inheritance

The <b>ID3D11RasterizerState1</b> interface inherits from <a href="/windows/desktop/api/d3d11/nn-d3d11-id3d11rasterizerstate">ID3D11RasterizerState</a>. <b>ID3D11RasterizerState1</b> also has these types of members:

## -remarks

To create a rasterizer-state object, call <a href="/windows/desktop/api/d3d11_1/nf-d3d11_1-id3d11device1-createrasterizerstate1">ID3D11Device1::CreateRasterizerState1</a>. To bind the rasterizer-state object to the <a href="/windows/desktop/direct3d11/d3d10-graphics-programming-guide-rasterizer-stage">rasterizer stage</a>, call <a href="/windows/desktop/api/d3d11/nf-d3d11-id3d11devicecontext-rssetstate">ID3D11DeviceContext::RSSetState</a>.

## -see-also

<a href="/windows/desktop/direct3d11/d3d11-graphics-reference-d3d11-core-interfaces">Core Interfaces</a>



<a href="/windows/desktop/api/d3d11/nn-d3d11-id3d11rasterizerstate">ID3D11RasterizerState</a>