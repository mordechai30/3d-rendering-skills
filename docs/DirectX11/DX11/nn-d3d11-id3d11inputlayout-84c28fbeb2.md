Source: [https://learn.microsoft.com/en-us/windows/win32/api/d3d11/nn-d3d11-id3d11inputlayout](<https://learn.microsoft.com/en-us/windows/win32/api/d3d11/nn-d3d11-id3d11inputlayout>)

# ID3D11InputLayout interface


## -description

An input-layout interface holds a definition of how to feed vertex data that is laid out in memory into the <a href="/windows/desktop/direct3d11/d3d10-graphics-programming-guide-input-assembler-stage">input-assembler stage</a> of the <a href="/windows/desktop/direct3d11/overviews-direct3d-11-graphics-pipeline">graphics pipeline</a>.

## -remarks

To create an input-layout object, call <a href="/windows/desktop/api/d3d11/nf-d3d11-id3d11device-createinputlayout">ID3D11Device::CreateInputLayout</a>. To bind the input-layout object to the <a href="/windows/desktop/direct3d11/d3d10-graphics-programming-guide-input-assembler-stage">input-assembler stage</a>, call <a href="/windows/desktop/api/d3d11/nf-d3d11-id3d11devicecontext-iasetinputlayout">ID3D11DeviceContext::IASetInputLayout</a>.

## -see-also

<a href="/windows/desktop/direct3d11/d3d11-graphics-reference-d3d11-core-interfaces">Core Interfaces</a>



<a href="/windows/desktop/api/d3d11/nn-d3d11-id3d11devicechild">ID3D11DeviceChild</a>