Source: [https://learn.microsoft.com/en-us/windows/win32/direct3d11/id3dx11effect-gettechniquebyname](<https://learn.microsoft.com/en-us/windows/win32/direct3d11/id3dx11effect-gettechniquebyname>)

# ID3DX11Effect::GetTechniqueByName method

Get a technique by name.

## Syntax


```C++
ID3DX11EffectTechnique* GetTechniqueByName(
   LPCSTR Name
);
```



## Parameters

<dl> <dt>

*Name* 
</dt> <dd>

Type: **[**LPCSTR**](/windows/desktop/WinProg/windows-data-types)**

The name of the technique.

</dd> </dl>

## Return value

Type: **[**ID3DX11EffectTechnique**](./id3dx11effecttechnique-b79e863e91.md)\***

A pointer to an [**ID3DX11EffectTechnique**](./id3dx11effecttechnique-b79e863e91.md). If a technique with the appropriate name is not found an invalid technique is returned. [**ID3DX11EffectTechnique::IsValid**](./id3dx11effecttechnique-isvalid-d9ba85630d.md) should be called on the returned technique to determine whether it is valid.

## Remarks

An effect contains one or more techniques; each technique contains one or more passes. You can access a technique using its name or with an index.

> [!Note]  
> The DirectX SDK does not supply any compiled binaries for effects. You must use Effects 11 source to build your effects-type application. For more information about using Effects 11 source, see [Differences Between Effects 10 and Effects 11](./d3d11-graphics-programming-guide-effects-differences-f7025c8c69.md).

 

## Requirements



| Requirement | Value |
|--------------------|----------------------------------------------------------------------------------------------------------------------------------------------|
| Header<br/>  | <dl> <dt>D3dx11effect.h</dt> </dl>                                                    |
| Library<br/> | <dl> <dt>N/A (An Effects 11 library is available online as shared source.)</dt> </dl> |



## See also

<dl> <dt>

[ID3DX11Effect](./id3dx11effect-277b450b03.md)
</dt> </dl>