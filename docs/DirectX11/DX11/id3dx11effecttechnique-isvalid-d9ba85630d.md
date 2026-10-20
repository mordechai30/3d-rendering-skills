Source: [https://learn.microsoft.com/en-us/windows/win32/direct3d11/id3dx11effecttechnique-isvalid](<https://learn.microsoft.com/en-us/windows/win32/direct3d11/id3dx11effecttechnique-isvalid>)

# ID3DX11EffectTechnique::IsValid method

Test a technique to see if it contains valid syntax.

## Syntax


```C++
BOOL IsValid();
```



## Parameters

This method has no parameters.

## Return value

Type: **[**BOOL**](/windows/desktop/WinProg/windows-data-types)**

**TRUE** if the code syntax is valid; otherwise **FALSE**.

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

[ID3DX11EffectTechnique](./id3dx11effecttechnique-b79e863e91.md)
</dt> </dl>