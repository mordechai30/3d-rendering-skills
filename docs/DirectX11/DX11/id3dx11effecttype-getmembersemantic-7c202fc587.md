Source: [https://learn.microsoft.com/en-us/windows/win32/direct3d11/id3dx11effecttype-getmembersemantic](<https://learn.microsoft.com/en-us/windows/win32/direct3d11/id3dx11effecttype-getmembersemantic>)

# ID3DX11EffectType::GetMemberSemantic method

Get the semantic attached to a member.

## Syntax


```C++
LPCSTR GetMemberSemantic(
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

Type: **[**LPCSTR**](/windows/desktop/WinProg/windows-data-types)**

A string that contains the semantic.

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

[ID3DX11EffectType](./id3dx11effecttype-fd26b9b277.md)
</dt> </dl>