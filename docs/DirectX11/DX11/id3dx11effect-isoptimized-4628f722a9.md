Source: [https://learn.microsoft.com/en-us/windows/win32/direct3d11/id3dx11effect-isoptimized](<https://learn.microsoft.com/en-us/windows/win32/direct3d11/id3dx11effect-isoptimized>)

# ID3DX11Effect::IsOptimized method

Test an effect to see if the reflection metadata has been removed from memory.

## Syntax


```C++
BOOL IsOptimized();
```



## Parameters

This method has no parameters.

## Return value

Type: **[**BOOL**](/windows/desktop/WinProg/windows-data-types)**

**TRUE** if the effect is optimized; otherwise **FALSE**.

## Remarks

An effect uses memory space two different ways: to store the information required by the runtime to execute an effect, and to store the metadata required to reflect information back to an application using the API. You can minimize the amount of memory required by an effect by calling [**ID3DX11Effect::Optimize**](./id3dx11effect-optimize-a77a6c58cc.md) which removes the reflection metadata from memory. Of course, API methods to read variables will no longer work once reflection data has been removed.

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