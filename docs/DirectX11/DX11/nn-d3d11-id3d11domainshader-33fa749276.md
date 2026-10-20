Source: [https://learn.microsoft.com/en-us/windows/win32/api/d3d11/nn-d3d11-id3d11domainshader](<https://learn.microsoft.com/en-us/windows/win32/api/d3d11/nn-d3d11-id3d11domainshader>)

# ID3D11DomainShader interface


## -description

A domain-shader interface manages an executable program (a domain shader) that controls the domain-shader stage.

## -remarks

The domain-shader interface has no methods; use HLSL to implement your shader functionality. All shaders are implemented from a common set of features referred to as the common-shader core..

To create a domain-shader interface, call <a href="/windows/desktop/api/d3d11/nf-d3d11-id3d11device-createdomainshader">ID3D11Device::CreateDomainShader</a>. Before using a domain shader you must bind it to the device by calling <a href="/windows/desktop/api/d3d11/nf-d3d11-id3d11devicecontext-dssetshader">ID3D11DeviceContext::DSSetShader</a>.

This interface is defined in D3D11.h.

## -see-also

<a href="/windows/desktop/api/d3d11/nn-d3d11-id3d11devicechild">ID3D11DeviceChild</a>



<a href="/windows/desktop/direct3d11/d3d11-graphics-reference-d3d11-shader-interfaces">Shader Interfaces</a>