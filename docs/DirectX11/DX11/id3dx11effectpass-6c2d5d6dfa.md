Source: [https://learn.microsoft.com/en-us/windows/win32/direct3d11/id3dx11effectpass](<https://learn.microsoft.com/en-us/windows/win32/direct3d11/id3dx11effectpass>)

# ID3DX11EffectPass interface

An **ID3DX11EffectPass** interface encapsulates state assignments within a technique.

The lifetime of an **ID3DX11EffectPass** object is equal to the lifetime of its parent [**ID3DX11Effect**](./id3dx11effect-277b450b03.md) object.

-   [Methods](#methods)

### Methods

The **ID3DX11EffectPass** interface has these methods.



| Method                                                                   | Description                                                       |
|:-------------------------------------------------------------------------|:------------------------------------------------------------------|
| [**Apply**](./id3dx11effectpass-apply-dd53695d81.md)                                 | Set the state contained in a pass to the device.<br/>       |
| [**ComputeStateBlockMask**](./id3dx11effectpass-computestateblockmask-c572491322.md) | Generate a mask for allowing/preventing state changes.<br/> |
| [**GetAnnotationByIndex**](./id3dx11effectpass-getannotationbyindex-f329f88c79.md)   | Get an annotation by index.<br/>                            |
| [**GetAnnotationByName**](./id3dx11effectpass-getannotationbyname-f554b81e68.md)     | Get an annotation by name.<br/>                             |
| [**GetComputeShaderDesc**](./id3dx11effectpass-getcomputeshaderdesc-f30cf4b37b.md)   | Get a compute-shader description.<br/>                      |
| [**GetDesc**](./id3dx11effectpass-getdesc-ba903790ee.md)                             | Get a pass description.<br/>                                |
| [**GetDomainShaderDesc**](./id3dx11effectpass-getdomainshaderdesc-0db3ce5346.md)     | Get a domain-shader description.<br/>                       |
| [**GetGeometryShaderDesc**](./id3dx11effectpass-getgeometryshaderdesc-826e75a17d.md) | Get a geometry-shader description.<br/>                     |
| [**GetHullShaderDesc**](./id3dx11effectpass-gethullshaderdesc-6b1e7cf94b.md)         | Get hull-shader description.<br/>                           |
| [**GetPixelShaderDesc**](./id3dx11effectpass-getpixelshaderdesc-65d9305eb2.md)       | Get a pixel-shader description.<br/>                        |
| [**GetVertexShaderDesc**](./id3dx11effectpass-getvertexshaderdesc-6c9c728cbb.md)     | Get a vertex-shader description.<br/>                       |
| [**IsValid**](./id3dx11effectpass-isvalid-d437555a83.md)                             | Test a pass to see if it contains valid syntax.<br/>        |



 

## Remarks

A pass is a block of code that sets render-state objects and shaders. A pass is declared within a technique.

To get an effect-pass interface, call a method like [**ID3DX11EffectTechnique::GetPassByName**](./id3dx11effecttechnique-getpassbyname-36892c37a0.md).

> [!Note]  
> The DirectX SDK does not supply any compiled binaries for effects. You must use Effects 11 source to build your effects-type application. For more information about using Effects 11 source, see [Differences Between Effects 10 and Effects 11](./d3d11-graphics-programming-guide-effects-differences-f7025c8c69.md).

 

## Requirements



| Requirement | Value |
|--------------------|----------------------------------------------------------------------------------------------------------------------------------------------|
| Header<br/>  | <dl> <dt>D3dx11effect.h</dt> </dl>                                                    |
| Library<br/> | <dl> <dt>N/A (An Effects 11 library is available online as shared source.)</dt> </dl> |



## See also

<dl> <dt>

[Effects 11 Interfaces](./d3d11-graphics-reference-effects11-interfaces-5b7b91a9df.md)
</dt> <dt>

[D3DX Interfaces](./d3d11-graphics-reference-d3dx11-interfaces-bf8653ed03.md)
</dt> </dl>