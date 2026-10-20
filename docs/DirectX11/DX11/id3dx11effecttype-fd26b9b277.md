Source: [https://learn.microsoft.com/en-us/windows/win32/direct3d11/id3dx11effecttype](<https://learn.microsoft.com/en-us/windows/win32/direct3d11/id3dx11effecttype>)

# ID3DX11EffectType interface

The **ID3DX11EffectType** interface accesses effect variables by type.

The lifetime of an **ID3DX11EffectType** object is equal to the lifetime of its parent [**ID3DX11Effect**](./id3dx11effect-277b450b03.md) object.

-   [Methods](#methods)

### Methods

The **ID3DX11EffectType** interface has these methods.



| Method                                                                       | Description                                       |
|:-----------------------------------------------------------------------------|:--------------------------------------------------|
| [**GetDesc**](./id3dx11effecttype-getdesc-5c6cd0fda2.md)                                 | Get an effect-type description.<br/>        |
| [**GetMemberName**](./id3dx11effecttype-getmembername-0558e9a72c.md)                     | Get the name of a member.<br/>              |
| [**GetMemberSemantic**](./id3dx11effecttype-getmembersemantic-7c202fc587.md)             | Get the semantic attached to a member.<br/> |
| [**GetMemberTypeByIndex**](./id3dx11effecttype-getmembertypebyindex-4b295e5828.md)       | Get a member type by index.<br/>            |
| [**GetMemberTypeByName**](./id3dx11effecttype-getmembertypebyname-4d413f4259.md)         | Get a member type by name.<br/>            |
| [**GetMemberTypeBySemantic**](./id3dx11effecttype-getmembertypebysemantic-abe3d220c3.md) | Get a member type by semantic.<br/>         |
| [**IsValid**](./id3dx11effecttype-isvalid-ec3fa0c8dc.md)                                 | Tests that the effect type is valid.<br/>   |



 

## Remarks

To get information about an effect type from an effect variable, call [**ID3DX11EffectVariable::GetType**](./id3dx11effectvariable-gettype-9801c6e6a1.md).

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