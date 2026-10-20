Source: [https://learn.microsoft.com/en-us/windows/win32/direct3d11/id3dx11effectgroup-gettechniquebyindex](<https://learn.microsoft.com/en-us/windows/win32/direct3d11/id3dx11effectgroup-gettechniquebyindex>)

# ID3DX11EffectGroup::GetTechniqueByIndex method

Get a technique by index.

## Syntax


```C++
ID3DX11EffectTechnique* GetTechniqueByIndex(
   UINT Index
);
```



## Parameters

<dl> <dt>

*Index* 
</dt> <dd>

Type: **[**UINT**](/windows/desktop/WinProg/windows-data-types)**

A zero-based index.

</dd> </dl>

## Return value

Type: **[**ID3DX11EffectTechnique**](./id3dx11effecttechnique-b79e863e91.md)\***

A pointer to an [**ID3DX11EffectTechnique**](./id3dx11effecttechnique-b79e863e91.md).

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

[ID3DX11EffectGroup](./id3dx11effectgroup-2a6f9fee4c.md)
</dt> </dl>