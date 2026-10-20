Source: [https://learn.microsoft.com/en-us/windows/win32/direct3d11/id3dx11effectvariable-isvalid](<https://learn.microsoft.com/en-us/windows/win32/direct3d11/id3dx11effectvariable-isvalid>)

# ID3DX11EffectVariable::IsValid method

Compare the data type with the data stored.

## Syntax


```C++
BOOL IsValid();
```



## Parameters

This method has no parameters.

## Return value

Type: **[**BOOL**](/windows/desktop/WinProg/windows-data-types)**

**TRUE** if the syntax is valid; otherwise **FALSE**.

## Remarks

This method checks that the data type matches the data stored after casting one interface to another (using any of the As methods).

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