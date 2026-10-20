Source: [https://learn.microsoft.com/en-us/windows/win32/api/d3d11/nn-d3d11-id3d11pixelshader](<https://learn.microsoft.com/en-us/windows/win32/api/d3d11/nn-d3d11-id3d11pixelshader>)

# ID3D11PixelShader interface


## -description

A pixel-shader interface manages an executable program (a pixel shader) that controls the pixel-shader stage.

## -remarks

The pixel-shader interface has no methods; use HLSL to implement your shader functionality. All shaders in are implemented from a common set of features referred to as the common-shader core..

To create a pixel shader interface, call <a href="/windows/desktop/api/d3d11/nf-d3d11-id3d11device-createpixelshader">ID3D11Device::CreatePixelShader</a>. Before using a pixel shader you must bind it to the device by calling <a href="/windows/desktop/api/d3d11/nf-d3d11-id3d11devicecontext-pssetshader">ID3D11DeviceContext::PSSetShader</a>.

This interface is defined in D3D11.h.

## -see-also

<a href="/windows/desktop/api/d3d11/nn-d3d11-id3d11devicechild">ID3D11DeviceChild</a>



<a href="/windows/desktop/direct3d11/d3d11-graphics-reference-d3d11-shader-interfaces">Shader Interfaces</a>