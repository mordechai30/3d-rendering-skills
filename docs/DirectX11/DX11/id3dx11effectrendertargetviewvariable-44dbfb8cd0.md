Source: [https://learn.microsoft.com/en-us/windows/win32/direct3d11/id3dx11effectrendertargetviewvariable](<https://learn.microsoft.com/en-us/windows/win32/direct3d11/id3dx11effectrendertargetviewvariable>)

# ID3DX11EffectRenderTargetViewVariable interface

A render-target-view interface accesses a render target.

## Members

The **ID3DX11EffectRenderTargetViewVariable** interface inherits from [**ID3DX11EffectRasterizerVariable**](./id3dx11effectvariable-89fd46cf57.md). **ID3DX11EffectRenderTargetViewVariable** also has these types of members:

-   [Methods](#methods)

### Methods

The **ID3DX11EffectRenderTargetViewVariable** interface has these methods.



| Method                                                                                     | Description                                |
|:-------------------------------------------------------------------------------------------|:-------------------------------------------|
| [**GetRenderTarget**](./id3dx11effectrendertargetviewvariable-getrendertarget-ecd1a09d75.md)           | Get a render-target.<br/>            |
| [**GetRenderTargetArray**](./id3dx11effectrendertargetviewvariable-getrendertargetarray-057848f3f6.md) | Get an array of render-targets.<br/> |
| [**SetRenderTarget**](./id3dx11effectrendertargetviewvariable-setrendertarget-9c136b939e.md)           | Set a render-target.<br/>            |
| [**SetRenderTargetArray**](./id3dx11effectrendertargetviewvariable-setrendertargetarray-df1bd459be.md) | Set an array of render-targets.<br/> |



 

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

[**ID3DX11EffectRasterizerVariable**](./id3dx11effectvariable-89fd46cf57.md)
</dt> <dt>

[Effects 11 Interfaces](./d3d11-graphics-reference-effects11-interfaces-5b7b91a9df.md)
</dt> <dt>

[D3DX Interfaces](./d3d11-graphics-reference-d3dx11-interfaces-bf8653ed03.md)
</dt> </dl>