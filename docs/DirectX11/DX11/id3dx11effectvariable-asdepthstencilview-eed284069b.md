Source: [https://learn.microsoft.com/en-us/windows/win32/direct3d11/id3dx11effectvariable-asdepthstencilview](<https://learn.microsoft.com/en-us/windows/win32/direct3d11/id3dx11effectvariable-asdepthstencilview>)

# ID3DX11EffectVariable::AsDepthStencilView method

Get a depth-stencil-view variable.

## Syntax


```C++
ID3DX11EffectDepthStencilViewVariable* AsDepthStencilView();
```



## Parameters

This method has no parameters.

## Return value

Type: **[**ID3DX11EffectDepthStencilViewVariable**](./id3dx11effectdepthstencilviewvariable-0b6e536a0c.md)\***

A pointer to a depth-stencil-view variable. See [**ID3DX11EffectDepthStencilViewVariable**](./id3dx11effectdepthstencilviewvariable-0b6e536a0c.md).

## Remarks

This method returns a version of the effect variable that has been specialized to a depth-stencil-view variable. Similar to a cast, this specialization will return an invalid object if the effect variable does not contain depth-stencil-view data.

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