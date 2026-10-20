Source: [https://learn.microsoft.com/en-us/windows/win32/direct3d11/id3dx11effectshadervariable](<https://learn.microsoft.com/en-us/windows/win32/direct3d11/id3dx11effectshadervariable>)

# ID3DX11EffectShaderVariable interface

A shader-variable interface accesses a shader variable.

## Members

The **ID3DX11EffectShaderVariable** interface inherits from [**ID3DX11EffectVariable**](./id3dx11effectvariable-89fd46cf57.md). **ID3DX11EffectShaderVariable** also has these types of members:

-   [Methods](#methods)

### Methods

The **ID3DX11EffectShaderVariable** interface has these methods.



| Method                                                                                                           | Description                                            |
|:-----------------------------------------------------------------------------------------------------------------|:-------------------------------------------------------|
| [**GetComputeShader**](./id3dx11effectshadervariable-getcomputeshader-733d9e7c95.md)                                         | Get a compute shader.<br/>                       |
| [**GetDomainShader**](./id3dx11effectshadervariable-getdomainshader-23189f6651.md)                                           | Get a domain shader.<br/>                        |
| [**GetGeometryShader**](./id3dx11effectshadervariable-getgeometryshader-85cd8ae711.md)                                       | Get a geometry shader.<br/>                      |
| [**GetHullShader**](./id3dx11effectshadervariable-gethullshader-164d1ed593.md)                                               | Get a hull shader.<br/>                          |
| [**GetInputSignatureElementDesc**](./id3dx11effectshadervariable-getinputsignatureelementdesc-ce9f2e7f63.md)                 | Get an input-signature description.<br/>         |
| [**GetOutputSignatureElementDesc**](./id3dx11effectshadervariable-getoutputsignatureelementdesc-d6f0197f38.md)               | Get an output-signature description.<br/>        |
| [**GetPatchConstantSignatureElementDesc**](./id3dx11effectshadervariable-getpatchconstantsignatureelementdesc-0fb78d7df6.md) | Get a patch constant signature description.<br/> |
| [**GetPixelShader**](./id3dx11effectshadervariable-getpixelshader-1b43e30ee6.md)                                             | Get a pixel shader.<br/>                         |
| [**GetShaderDesc**](./id3dx11effectshadervariable-getshaderdesc-223bee1b14.md)                                               | Get a shader description.<br/>                   |
| [**GetVertexShader**](./id3dx11effectshadervariable-getvertexshader-e0e0cde7fd.md)                                           | Get a vertex shader.<br/>                        |



 

## Remarks

> [!Note]  
> The DirectX SDK does not supply any compiled binaries for effects. You must use Effects 11 source to build your effects-type application. For more information about using Effects 11 source, see [Differences Between Effects 10 and Effects 11](./d3d11-graphics-programming-guide-effects-differences-f7025c8c69.md).

 

## Requirements



| Requirement | Value |
|--------------------|----------------------------------------------------------------------------------------------------------------------------------------------|
| Header<br/>  | <dl> <dt>D3dx11effect.h</dt> </dl>                                                    |
| Library<br/> | <dl> <dt>N/A (An Effects 11 library is available online as shared source.)</dt> </dl> |



## See also

<dl> <dt>

[**ID3DX11EffectVariable**](./id3dx11effectvariable-89fd46cf57.md)
</dt> <dt>

[Effects 11 Interfaces](./d3d11-graphics-reference-effects11-interfaces-5b7b91a9df.md)
</dt> <dt>

[D3DX Interfaces](./d3d11-graphics-reference-d3dx11-interfaces-bf8653ed03.md)
</dt> </dl>