Source: [https://learn.microsoft.com/en-us/windows/win32/api/D3D11ShaderTracing/nn-d3d11shadertracing-id3d11shadertracefactory](<https://learn.microsoft.com/en-us/windows/win32/api/D3D11ShaderTracing/nn-d3d11shadertracing-id3d11shadertracefactory>)

# ID3D11ShaderTraceFactory interface


## -description

An <b>ID3D11ShaderTraceFactory</b> interface implements a method for generating shader trace information objects.

## -inheritance

The <b>ID3D11ShaderTraceFactory</b> interface inherits from the <a href="/windows/desktop/api/unknwn/nn-unknwn-iunknown">IUnknown</a> interface. <b>ID3D11ShaderTraceFactory</b> also has these types of members:

## -remarks

These APIs require the Windows Software Development Kit (SDK) for Windows 8.

To retrieve an instance of <b>ID3D11ShaderTraceFactory</b>, call <a href="/windows/desktop/api/unknwn/nf-unknwn-iunknown-queryinterface(q)">IUnknown::QueryInterface</a> on a <a href="/windows/desktop/api/d3d11/nn-d3d11-id3d11device">ID3D11Device</a> that you created with <a href="/windows/desktop/api/d3d11/ne-d3d11-d3d11_create_device_flag">D3D11_CREATE_DEVICE_DEBUGGABLE</a>.

## -see-also

<a href="/windows/desktop/api/unknwn/nn-unknwn-iunknown">IUnknown</a>



<a href="/windows/desktop/direct3d11/d3d11-graphics-reference-d3d11-shader-interfaces">Shader Interfaces</a>