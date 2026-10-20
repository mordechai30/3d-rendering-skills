Source: [https://learn.microsoft.com/en-us/windows/win32/api/D3D11_1/nn-d3d11_1-id3d11blendstate1](<https://learn.microsoft.com/en-us/windows/win32/api/D3D11_1/nn-d3d11_1-id3d11blendstate1>)

# ID3D11BlendState1 interface


## -description

The blend-state interface holds a description for blending state that you can bind to the <a href="/windows/desktop/direct3d11/d3d10-graphics-programming-guide-output-merger-stage">output-merger stage</a>. This blend-state interface supports logical operations as well as blending operations.

## -inheritance

The <b>ID3D11BlendState1</b> interface inherits from <a href="/windows/desktop/api/d3d11/nn-d3d11-id3d11blendstate">ID3D11BlendState</a>. <b>ID3D11BlendState1</b> also has these types of members:

## -remarks

Blending applies a simple function to combine output values from a pixel shader with data in a render target. You have control over how the pixels are blended by using a predefined set of blending operations and preblending operations.

To create a blend-state object, call <a href="/windows/desktop/api/d3d11_1/nf-d3d11_1-id3d11device1-createblendstate1">ID3D11Device1::CreateBlendState1</a>. To bind the blend-state object to the <a href="/windows/desktop/direct3d11/d3d10-graphics-programming-guide-output-merger-stage">output-merger stage</a>, call <a href="/windows/desktop/api/d3d11/nf-d3d11-id3d11devicecontext-omsetblendstate">ID3D11DeviceContext::OMSetBlendState</a>.

## -see-also

<a href="/windows/desktop/direct3d11/d3d11-graphics-reference-d3d11-core-interfaces">Core Interfaces</a>



<a href="/windows/desktop/api/d3d11/nn-d3d11-id3d11blendstate">ID3D11BlendState</a>