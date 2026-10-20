Source: [https://learn.microsoft.com/en-us/windows/win32/api/d3d11/nn-d3d11-id3d11hullshader](<https://learn.microsoft.com/en-us/windows/win32/api/d3d11/nn-d3d11-id3d11hullshader>)

# ID3D11HullShader interface


## -description

A hull-shader interface manages an executable program (a hull shader) that controls the hull-shader stage.

## -remarks

The hull-shader interface has no methods; use HLSL to implement your shader functionality. All shaders are implemented from a common set of features referred to as the common-shader core..

To create a hull-shader interface, call <a href="/windows/desktop/api/d3d11/nf-d3d11-id3d11device-createhullshader">ID3D11Device::CreateHullShader</a>. Before using a hull shader you must bind it to the device by calling <a href="/windows/desktop/api/d3d11/nf-d3d11-id3d11devicecontext-hssetshader">ID3D11DeviceContext::HSSetShader</a>.

This interface is defined in D3D11.h.

## -see-also

<a href="/windows/desktop/api/d3d11/nn-d3d11-id3d11devicechild">ID3D11DeviceChild</a>



<a href="/windows/desktop/direct3d11/d3d11-graphics-reference-d3d11-shader-interfaces">Shader Interfaces</a>