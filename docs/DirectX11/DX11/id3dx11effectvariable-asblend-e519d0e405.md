Source: [https://learn.microsoft.com/en-us/windows/win32/direct3d11/id3dx11effectvariable-asblend](<https://learn.microsoft.com/en-us/windows/win32/direct3d11/id3dx11effectvariable-asblend>)

# ID3DX11EffectVariable::AsBlend method

Get an effect-blend variable.

## Syntax


```C++
ID3DX11EffectBlendVariable* AsBlend();
```



## Parameters

This method has no parameters.

## Return value

Type: **[**ID3DX11EffectBlendVariable**](./id3dx11effectblendvariable-1cac3f92ff.md)\***

A pointer to an effect blend variable. See [**ID3DX11EffectBlendVariable**](./id3dx11effectblendvariable-1cac3f92ff.md).

## Remarks

AsBlend returns a version of the effect variable that has been specialized to an effect-blend variable. Similar to a cast, this specialization will return an invalid object if the effect variable does not contain effect-blend data.

Applications can test the returned object for validity by calling [**IsValid**](./id3dx11effectvariable-isvalid-c0ad788b13.md).

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