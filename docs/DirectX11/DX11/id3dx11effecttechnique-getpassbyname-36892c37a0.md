Source: [https://learn.microsoft.com/en-us/windows/win32/direct3d11/id3dx11effecttechnique-getpassbyname](<https://learn.microsoft.com/en-us/windows/win32/direct3d11/id3dx11effecttechnique-getpassbyname>)

# ID3DX11EffectTechnique::GetPassByName method

Get a pass by name.

## Syntax


```C++
ID3DX11EffectPass* GetPassByName(
   LPCSTR Name
);
```



## Parameters

<dl> <dt>

*Name* 
</dt> <dd>

Type: **[**LPCSTR**](/windows/desktop/WinProg/windows-data-types)**

The name of the pass.

</dd> </dl>

## Return value

Type: **[**ID3DX11EffectPass**](./id3dx11effectpass-6c2d5d6dfa.md)\***

A pointer to an [**ID3DX11EffectPass**](./id3dx11effectpass-6c2d5d6dfa.md).

## Remarks

A technique contains one or more passes; get a pass using a name or an index.

> [!Note]  
> The DirectX SDK does not supply any compiled binaries for effects. You must use Effects 11 source to build your effects-type application. For more information about using Effects 11 source, see [Differences Between Effects 10 and Effects 11](./d3d11-graphics-programming-guide-effects-differences-f7025c8c69.md).

 

## Requirements



| Requirement | Value |
|--------------------|----------------------------------------------------------------------------------------------------------------------------------------------|
| Header<br/>  | <dl> <dt>D3dx11effect.h</dt> </dl>                                                    |
| Library<br/> | <dl> <dt>N/A (An Effects 11 library is available online as shared source.)</dt> </dl> |



## See also

<dl> <dt>

[ID3DX11EffectTechnique](./id3dx11effecttechnique-b79e863e91.md)
</dt> </dl>