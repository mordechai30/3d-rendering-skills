Source: [https://learn.microsoft.com/en-us/windows/win32/api/D3D11/nn-d3d11-id3d11samplerstate](<https://learn.microsoft.com/en-us/windows/win32/api/D3D11/nn-d3d11-id3d11samplerstate>)

# ID3D11SamplerState interface


## -description

The sampler-state interface holds a description for sampler state that you can bind to any shader stage of the <a href="/windows/desktop/direct3d11/overviews-direct3d-11-graphics-pipeline">pipeline</a> for reference by texture sample operations.

## -inheritance

The <b>ID3D11SamplerState</b> interface inherits from <a href="/windows/desktop/api/d3d11/nn-d3d11-id3d11devicechild">ID3D11DeviceChild</a>. <b>ID3D11SamplerState</b> also has these types of members:

## -remarks

To create a sampler-state object, call <a href="/windows/desktop/api/d3d11/nf-d3d11-id3d11device-createsamplerstate">ID3D11Device::CreateSamplerState</a>.

To bind a sampler-state object to any <a href="/windows/desktop/direct3d11/overviews-direct3d-11-graphics-pipeline">pipeline</a> shader stage, call the following methods:

<ul>
<li>
<a href="/windows/desktop/api/d3d11/nf-d3d11-id3d11devicecontext-vssetsamplers">ID3D11DeviceContext::VSSetSamplers</a>
</li>
<li>
<a href="/windows/desktop/api/d3d11/nf-d3d11-id3d11devicecontext-hssetsamplers">ID3D11DeviceContext::HSSetSamplers</a>
</li>
<li>
<a href="/windows/desktop/api/d3d11/nf-d3d11-id3d11devicecontext-dssetsamplers">ID3D11DeviceContext::DSSetSamplers</a>
</li>
<li>
<a href="/windows/desktop/api/d3d11/nf-d3d11-id3d11devicecontext-gssetsamplers">ID3D11DeviceContext::GSSetSamplers</a>
</li>
<li>
<a href="/windows/desktop/api/d3d11/nf-d3d11-id3d11devicecontext-pssetsamplers">ID3D11DeviceContext::PSSetSamplers</a>
</li>
<li>
<a href="/windows/desktop/api/d3d11/nf-d3d11-id3d11devicecontext-cssetsamplers">ID3D11DeviceContext::CSSetSamplers</a>
</li>
</ul>
You can bind the same sampler-state object to multiple shader stages simultaneously.

## -see-also

<a href="/windows/desktop/direct3d11/d3d11-graphics-reference-d3d11-core-interfaces">Core Interfaces</a>



<a href="/windows/desktop/api/d3d11/nn-d3d11-id3d11devicechild">ID3D11DeviceChild</a>