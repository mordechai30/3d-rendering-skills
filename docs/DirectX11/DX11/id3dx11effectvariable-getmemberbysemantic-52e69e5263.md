Source: [https://learn.microsoft.com/en-us/windows/win32/direct3d11/id3dx11effectvariable-getmemberbysemantic](<https://learn.microsoft.com/en-us/windows/win32/direct3d11/id3dx11effectvariable-getmemberbysemantic>)

# ID3DX11EffectVariable::GetMemberBySemantic method

Get a structure member by semantic.

## Syntax


```C++
ID3DX11EffectVariable* GetMemberBySemantic(
   LPCSTR Semantic
);
```



## Parameters

<dl> <dt>

*Semantic* 
</dt> <dd>

Type: **[**LPCSTR**](/windows/desktop/WinProg/windows-data-types)**

The semantic.

</dd> </dl>

## Return value

Type: **[**ID3DX11EffectVariable**](./id3dx11effectvariable-89fd46cf57.md)\***

A pointer to an [**ID3DX11EffectVariable**](./id3dx11effectvariable-89fd46cf57.md).

## Remarks

If the effect variable is an structure, use this method to look up a member by attached semantic.

> [!Note]  
> The DirectX SDK does not supply any compiled binaries for effects. You must use Effects 11 source to build your effects-type application. For more information about using Effects 11 source, see [Differences Between Effects 10 and Effects 11](./d3d11-graphics-programming-guide-effects-differences-f7025c8c69.md).

 

## Requirements



| Requirement | Value |
|--------------------|----------------------------------------------------------------------------------------------------------------------------------------------|
| Header<br/>  | <dl> <dt>D3dx11effect.h</dt> </dl>                                                    |
| Library<br/> | <dl> <dt>N/A (An Effects 11 library is available online as shared source.)</dt> </dl> |



## See also

<dl> <dt>

[ID3DX11EffectVariable](./id3dx11effectvariable-89fd46cf57.md)
</dt> </dl>