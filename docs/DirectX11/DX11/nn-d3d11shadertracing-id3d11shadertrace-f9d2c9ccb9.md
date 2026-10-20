Source: [https://learn.microsoft.com/en-us/windows/win32/api/D3D11ShaderTracing/nn-d3d11shadertracing-id3d11shadertrace](<https://learn.microsoft.com/en-us/windows/win32/api/D3D11ShaderTracing/nn-d3d11shadertracing-id3d11shadertrace>)

# ID3D11ShaderTrace interface


## -description

An <b>ID3D11ShaderTrace</b> interface implements methods for obtaining traces of shader executions.

## -inheritance

The <b>ID3D11ShaderTrace</b> interface inherits from the <a href="/windows/desktop/api/unknwn/nn-unknwn-iunknown">IUnknown</a> interface. <b>ID3D11ShaderTrace</b> also has these types of members:

## -remarks

To retrieve an instance of <b>ID3D11ShaderTrace</b>, call the <a href="/windows/desktop/api/d3d11shadertracing/nf-d3d11shadertracing-id3d11shadertracefactory-createshadertrace">ID3D11ShaderTraceFactory::CreateShaderTrace</a> method. To retrieve an instance of <a href="/windows/desktop/api/d3d11shadertracing/nn-d3d11shadertracing-id3d11shadertracefactory">ID3D11ShaderTraceFactory</a>, call <a href="/windows/desktop/api/unknwn/nf-unknwn-iunknown-queryinterface(q)">IUnknown::QueryInterface</a> on a <a href="/windows/desktop/api/d3d11/nn-d3d11-id3d11device">ID3D11Device</a> that you created with <a href="/windows/desktop/api/d3d11/ne-d3d11-d3d11_create_device_flag">D3D11_CREATE_DEVICE_DEBUGGABLE</a>. Although shader tracing operates without setting <b>D3D11_CREATE_DEVICE_DEBUGGABLE</b>, we recommend that you create a shader debugging device because some devices (for example, <a href="/windows/desktop/direct3d11/overviews-direct3d-11-devices-create-warp">WARP</a> devices) might make behind-the-scenes shader optimizations that will lead to slightly incorrect shader traces when <b>D3D11_CREATE_DEVICE_DEBUGGABLE</b> isn't set.


All <b>ID3D11ShaderTrace</b> methods are thread safe.

All <b>ID3D11ShaderTrace</b> methods immediately force the reference device to flush rendering commands. Therefore, the most current trace status is always available on the reference device. That is, if you expect a trace to be ready after a draw operation, it will be ready.

<div class="alert"><b>Note</b>  This API requires the Windows Software Development Kit (SDK) for Windows 8.</div>
<div> </div>

## -see-also

<a href="/windows/desktop/api/unknwn/nn-unknwn-iunknown">IUnknown</a>



<a href="/windows/desktop/direct3d11/d3d11-graphics-reference-d3d11-shader-interfaces">Shader Interfaces</a>