Source: [https://learn.microsoft.com/en-us/windows/win32/direct3d11/id3dx11effectvariable-getparentconstantbuffer](<https://learn.microsoft.com/en-us/windows/win32/direct3d11/id3dx11effectvariable-getparentconstantbuffer>)

# ID3DX11EffectVariable::GetParentConstantBuffer method

Get a constant buffer.

## Syntax


```C++
ID3DX11EffectConstantBuffer* GetParentConstantBuffer();
```



## Parameters

This method has no parameters.

## Return value

Type: **[**ID3DX11EffectConstantBuffer**](./id3dx11effectconstantbuffer-ee6cbea9bf.md)\***

A pointer to a [**ID3DX11EffectConstantBuffer**](./id3dx11effectconstantbuffer-ee6cbea9bf.md).

## Remarks

Effect variables are read-from or written-to a constant buffer.

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