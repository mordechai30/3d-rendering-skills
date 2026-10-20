Source: [https://learn.microsoft.com/en-us/windows/win32/direct3d11/id3dx11effectvariable-asrendertargetview](<https://learn.microsoft.com/en-us/windows/win32/direct3d11/id3dx11effectvariable-asrendertargetview>)

# ID3DX11EffectVariable::AsRenderTargetView method

Get a render-target-view variable.

## Syntax


```C++
ID3DX11EffectRenderTargetViewVariable* AsRenderTargetView();
```



## Parameters

This method has no parameters.

## Return value

Type: **[**ID3DX11EffectRenderTargetViewVariable**](./id3dx11effectrendertargetviewvariable-44dbfb8cd0.md)\***

A pointer to a render-target-view variable. See [**ID3DX11EffectRenderTargetViewVariable**](./id3dx11effectrendertargetviewvariable-44dbfb8cd0.md).

## Remarks

This method returns a version of the effect variable that has been specialized to a render-target-view variable. Similar to a cast, this specialization will return an invalid object if the effect variable does not contain render-target-view data.

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