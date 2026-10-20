Source: [https://learn.microsoft.com/en-us/windows/win32/direct3d11/id3dx11effectgroup](<https://learn.microsoft.com/en-us/windows/win32/direct3d11/id3dx11effectgroup>)

# ID3DX11EffectGroup interface

The **ID3DX11EffectGroup** interface accesses an Effect group.

The lifetime of an **ID3DX11EffectGroup** object is equal to the lifetime of its parent [**ID3DX11Effect**](./id3dx11effect-277b450b03.md) object.

-   [Methods](#methods)

### Methods

The **ID3DX11EffectGroup** interface has these methods.



| Method                                                                  | Description                                                   |
|:------------------------------------------------------------------------|:--------------------------------------------------------------|
| [**GetAnnotationByIndex**](./id3dx11effectgroup-getannotationbyindex-82bfc04cc3.md) | Get an annotation by index.<br/>                        |
| [**GetAnnotationByName**](./id3dx11effectgroup-getannotationbyname-89eadc362b.md)   | Get an annotation by name.<br/>                         |
| [**GetDesc**](./id3dx11effectgroup-getdesc-10cd78fe37.md)                           | Gets a group description.<br/>                          |
| [**GetTechniqueByIndex**](./id3dx11effectgroup-gettechniquebyindex-9d88302951.md)   | Get a technique by index.<br/>                          |
| [**GetTechniqueByName**](./id3dx11effectgroup-gettechniquebyname-1371e66ad8.md)     | Get a technique by name.<br/>                           |
| [**IsValid**](./id3dx11effectgroup-isvalid-212505d831.md)                           | Test an effect to see if it contains valid syntax.<br/> |



 

## Remarks

To get an **ID3DX11EffectGroup** interface, call a method like [**ID3DX11Effect::GetGroupByName**](./id3dx11effect-getgroupbyname-82adac8249.md).

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