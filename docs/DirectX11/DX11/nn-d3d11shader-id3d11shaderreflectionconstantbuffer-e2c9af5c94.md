Source: [https://learn.microsoft.com/en-us/windows/win32/api/D3D11Shader/nn-d3d11shader-id3d11shaderreflectionconstantbuffer](<https://learn.microsoft.com/en-us/windows/win32/api/D3D11Shader/nn-d3d11shader-id3d11shaderreflectionconstantbuffer>)

# ID3D11ShaderReflectionConstantBuffer interface


## -description

This shader-reflection interface provides access to a constant buffer.

## -inheritance

The <b>ID3D11ShaderReflectionConstantBuffer</b> interface inherits from the <a href="/windows/desktop/api/unknwn/nn-unknwn-iunknown">IUnknown</a> interface. <b>ID3D11ShaderReflectionConstantBuffer</b> also has these types of members:
<ul>
<li><a href="/">Methods</a></li>
</ul>

## -remarks

To create a constant-buffer interface, call <a href="/windows/desktop/api/d3d11shader/nf-d3d11shader-id3d11shaderreflection-getconstantbufferbyindex">ID3D11ShaderReflection::GetConstantBufferByIndex</a> or <a href="/windows/desktop/api/d3d11shader/nf-d3d11shader-id3d11shaderreflection-getconstantbufferbyname">ID3D11ShaderReflection::GetConstantBufferByName</a>. This isn't a COM interface, so you don't need to worry about reference counts or releasing the interface when you're done with it.

## -see-also

<a href="/windows/desktop/direct3d11/d3d11-graphics-reference-d3d11-shader-interfaces">Shader Interfaces</a>