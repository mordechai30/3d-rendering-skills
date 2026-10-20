Source: [https://learn.microsoft.com/en-us/windows/win32/api/D3D11Shader/nn-d3d11shader-id3d11shaderreflectiontype](<https://learn.microsoft.com/en-us/windows/win32/api/D3D11Shader/nn-d3d11shader-id3d11shaderreflectiontype>)

# ID3D11ShaderReflectionType interface


## -description

This shader-reflection interface provides access to variable type.

## -inheritance

The <b>ID3D11ShaderReflectionType</b> interface inherits from the <a href="/windows/desktop/api/unknwn/nn-unknwn-iunknown">IUnknown</a> interface. <b>ID3D11ShaderReflectionType</b> also has these types of members:
<ul>
<li><a href="/">Methods</a></li>
</ul>

## -remarks

The get a shader-reflection-type interface, call <a href="/windows/desktop/api/d3d11shader/nf-d3d11shader-id3d11shaderreflectionvariable-gettype">ID3D11ShaderReflectionVariable::GetType</a>. This isn't a COM interface, so you don't need to worry about reference counts or releasing the interface when you're done with it.

## -see-also

<a href="/windows/desktop/direct3d11/d3d11-graphics-reference-d3d11-shader-interfaces">Shader Interfaces</a>