Source: [https://learn.microsoft.com/en-us/windows/win32/api/d3d11/nn-d3d11-id3d11vertexshader](<https://learn.microsoft.com/en-us/windows/win32/api/d3d11/nn-d3d11-id3d11vertexshader>)

# ID3D11VertexShader interface


## -description

A vertex-shader interface manages an executable program (a vertex shader) that controls the vertex-shader stage.

## -remarks

The vertex-shader interface has no methods; use HLSL to implement your shader functionality. All shaders are implemented from a common set of features referred to as the common-shader core..

To create a vertex shader interface, call <a href="/windows/desktop/api/d3d11/nf-d3d11-id3d11device-createvertexshader">ID3D11Device::CreateVertexShader</a>. Before using a vertex shader you must bind it to the device by calling <a href="/windows/desktop/api/d3d11/nf-d3d11-id3d11devicecontext-vssetshader">ID3D11DeviceContext::VSSetShader</a>.

This interface is defined in D3D11.h.

## -see-also

<a href="/windows/desktop/api/d3d11/nn-d3d11-id3d11devicechild">ID3D11DeviceChild</a>



<a href="/windows/desktop/direct3d11/d3d11-graphics-reference-d3d11-shader-interfaces">Shader Interfaces</a>