Source: [https://learn.microsoft.com/en-us/windows/win32/api/d3d11/nn-d3d11-id3d11computeshader](<https://learn.microsoft.com/en-us/windows/win32/api/d3d11/nn-d3d11-id3d11computeshader>)

# ID3D11ComputeShader interface


## -description

A compute-shader interface manages an executable program (a compute shader) that controls the compute-shader stage.

## -remarks

The compute-shader interface has no methods; use HLSL to implement your shader functionality. All shaders are implemented from a common set of features referred to as the common-shader core..

To create a compute-shader interface, call <a href="/windows/desktop/api/d3d11/nf-d3d11-id3d11device-createcomputeshader">ID3D11Device::CreateComputeShader</a>. Before using a compute shader you must bind it to the device by calling <a href="/windows/desktop/api/d3d11/nf-d3d11-id3d11devicecontext-cssetshader">ID3D11DeviceContext::CSSetShader</a>.

This interface is defined in D3D11.h.

## -see-also

<a href="/windows/desktop/api/d3d11/nn-d3d11-id3d11devicechild">ID3D11DeviceChild</a>



<a href="/windows/desktop/direct3d11/d3d11-graphics-reference-d3d11-shader-interfaces">Shader Interfaces</a>