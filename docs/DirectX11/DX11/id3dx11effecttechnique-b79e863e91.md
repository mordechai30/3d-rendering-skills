Source: [https://learn.microsoft.com/en-us/windows/win32/direct3d11/id3dx11effecttechnique](<https://learn.microsoft.com/en-us/windows/win32/direct3d11/id3dx11effecttechnique>)

# ID3DX11EffectTechnique interface

An **ID3DX11EffectTechnique** interface is a collection of passes.

The lifetime of an **ID3DX11EffectTechnique** object is equal to the lifetime of its parent [**ID3DX11Effect**](./id3dx11effect-277b450b03.md) object.

-   [Methods](#methods)

### Methods

The **ID3DX11EffectTechnique** interface has these methods.



| Method                                                                        | Description                                                           |
|:------------------------------------------------------------------------------|:----------------------------------------------------------------------|
| [**ComputeStateBlockMask**](./id3dx11effecttechnique-computestateblockmask-d23da8fd3e.md) | Compute a state-block mask to allow/prevent state changes.<br/> |
| [**GetAnnotationByIndex**](./id3dx11effecttechnique-getannotationbyindex-a0dae42dcd.md)   | Get an annotation by index.<br/>                                |
| [**GetAnnotationByName**](./id3dx11effecttechnique-getannotationbyname-81f102ba21.md)     | Get an annotation by name.<br/>                                 |
| [**GetDesc**](./id3dx11effecttechnique-getdesc-6543c44078.md)                             | Get a technique description.<br/>                               |
| [**GetPassByIndex**](./id3dx11effecttechnique-getpassbyindex-def70ec55f.md)               | Get a pass by index.<br/>                                       |
| [**GetPassByName**](./id3dx11effecttechnique-getpassbyname-36892c37a0.md)                 | Get a pass by name.<br/>                                        |
| [**IsValid**](./id3dx11effecttechnique-isvalid-d9ba85630d.md)                             | Test a technique to see if it contains valid syntax.<br/>       |



 

## Remarks

An effect contains one or more techniques; each technique contains one or more passes; each pass contains state assignments.

To get an effect-technique interface, call a method such as [**ID3DX11Effect::GetTechniqueByName**](./id3dx11effect-gettechniquebyname-32f1c521b9.md).

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