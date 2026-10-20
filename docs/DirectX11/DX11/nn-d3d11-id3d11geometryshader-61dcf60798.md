Source: [https://learn.microsoft.com/en-us/windows/win32/api/d3d11/nn-d3d11-id3d11geometryshader](<https://learn.microsoft.com/en-us/windows/win32/api/d3d11/nn-d3d11-id3d11geometryshader>)

# ID3D11GeometryShader interface


## -description

A geometry-shader interface manages an executable program (a geometry shader) that controls the geometry-shader stage.

## -remarks

The geometry-shader interface has no methods; use HLSL to implement your shader functionality. All shaders are implemented from a common set of features referred to as the common-shader core..

To create a geometry shader interface, call either <a href="/windows/desktop/api/d3d11/nf-d3d11-id3d11device-creategeometryshader">ID3D11Device::CreateGeometryShader</a> or <a href="/windows/desktop/api/d3d11/nf-d3d11-id3d11device-creategeometryshaderwithstreamoutput">ID3D11Device::CreateGeometryShaderWithStreamOutput</a>. Before using a geometry shader you must bind it to the device by calling <a href="/windows/desktop/api/d3d11/nf-d3d11-id3d11devicecontext-gssetshader">ID3D11DeviceContext::GSSetShader</a>.

This interface is defined in D3D11.h.

## -see-also

<a href="/windows/desktop/api/d3d11/nn-d3d11-id3d11devicechild">ID3D11DeviceChild</a>



<a href="/windows/desktop/direct3d11/d3d11-graphics-reference-d3d11-shader-interfaces">Shader Interfaces</a>