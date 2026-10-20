Source: [https://learn.microsoft.com/en-us/windows/win32/direct3d11/id3dx11effectvariable-getmemberbyindex](<https://learn.microsoft.com/en-us/windows/win32/direct3d11/id3dx11effectvariable-getmemberbyindex>)

# ID3DX11EffectVariable::GetMemberByIndex method

Get a structure member by index.

## Syntax


```C++
ID3DX11EffectVariable* GetMemberByIndex(
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

Type: **[**ID3DX11EffectVariable**](./id3dx11effectvariable-89fd46cf57.md)\***

A pointer to an [**ID3DX11EffectVariable**](./id3dx11effectvariable-89fd46cf57.md).

## Remarks

If the effect variable is an structure, use this method to look up a member by index.

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