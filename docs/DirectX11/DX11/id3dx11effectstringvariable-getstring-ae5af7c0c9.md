Source: [https://learn.microsoft.com/en-us/windows/win32/direct3d11/id3dx11effectstringvariable-getstring](<https://learn.microsoft.com/en-us/windows/win32/direct3d11/id3dx11effectstringvariable-getstring>)

# ID3DX11EffectStringVariable::GetString method

Get the string.

## Syntax


```C++
HRESULT GetString(
   LPCSTR *ppString
);
```



## Parameters

<dl> <dt>

*ppString* 
</dt> <dd>

Type: **[**LPCSTR**](/windows/desktop/WinProg/windows-data-types)\***

A pointer to the string.

</dd> </dl>

## Return value

Type: **[**HRESULT**](https://msdn.microsoft.com/library/Bb401631(v=MSDN.10).aspx)**

Returns one of the following [Direct3D 11 Return Codes](./d3d11-graphics-reference-returnvalues-2d2638a6a7.md).

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

[ID3DX11EffectStringVariable](./id3dx11effectstringvariable-0a2d7dee98.md)
</dt> </dl>