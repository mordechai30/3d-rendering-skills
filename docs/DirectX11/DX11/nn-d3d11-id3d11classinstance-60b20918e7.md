Source: [https://learn.microsoft.com/en-us/windows/win32/api/D3D11/nn-d3d11-id3d11classinstance](<https://learn.microsoft.com/en-us/windows/win32/api/D3D11/nn-d3d11-id3d11classinstance>)

# ID3D11ClassInstance interface


## -description

This interface encapsulates an HLSL class.

## -inheritance

The <b>ID3D11ClassInstance</b> interface inherits from <a href="/windows/desktop/api/d3d11/nn-d3d11-id3d11devicechild">ID3D11DeviceChild</a>. <b>ID3D11ClassInstance</b> also has these types of members:

## -remarks

This interface is created by calling <a href="/windows/desktop/api/d3d11/nf-d3d11-id3d11classlinkage-createclassinstance">ID3D11ClassLinkage::CreateClassInstance</a>. The interface is used when binding shader resources to the pipeline using APIs such as <a href="/windows/desktop/api/d3d11/nf-d3d11-id3d11devicecontext-vssetshader">ID3D11DeviceContext::VSSetShader</a>.

## -see-also

<a href="/windows/desktop/direct3d11/d3d11-graphics-reference-d3d11-core-interfaces">Core Interfaces</a>



<a href="/windows/desktop/api/d3d11/nn-d3d11-id3d11devicechild">ID3D11DeviceChild</a>



<a href="/windows/desktop/direct3d11/d3d11-graphics-reference-d3d11-shader-interfaces">Shader Interfaces</a>