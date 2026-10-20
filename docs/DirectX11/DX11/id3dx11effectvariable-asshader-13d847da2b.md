Source: [https://learn.microsoft.com/en-us/windows/win32/direct3d11/id3dx11effectvariable-asshader](<https://learn.microsoft.com/en-us/windows/win32/direct3d11/id3dx11effectvariable-asshader>)

# ID3DX11EffectVariable::AsShader method

Get a shader variable.

## Syntax


```C++
ID3DX11EffectShaderVariable* AsShader();
```



## Parameters

This method has no parameters.

## Return value

Type: **[**ID3DX11EffectShaderVariable**](./id3dx11effectshadervariable-81ab8d90dd.md)\***

A pointer to a shader variable. See [**ID3DX11EffectShaderVariable**](./id3dx11effectshadervariable-81ab8d90dd.md).

## Remarks

AsShader returns a version of the effect variable that has been specialized to a shader variable. Similar to a cast, this specialization will return an invalid object if the effect variable does not contain shader data.

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