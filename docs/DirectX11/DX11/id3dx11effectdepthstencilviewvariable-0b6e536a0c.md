Source: [https://learn.microsoft.com/en-us/windows/win32/direct3d11/id3dx11effectdepthstencilviewvariable](<https://learn.microsoft.com/en-us/windows/win32/direct3d11/id3dx11effectdepthstencilviewvariable>)

# ID3DX11EffectDepthStencilViewVariable interface

A depth-stencil-view-variable interface accesses a depth-stencil view.

## Members

The **ID3DX11EffectDepthStencilViewVariable** interface inherits from [**ID3DX11EffectVariable**](./id3dx11effectvariable-89fd46cf57.md). **ID3DX11EffectDepthStencilViewVariable** also has these types of members:

-   [Methods](#methods)

### Methods

The **ID3DX11EffectDepthStencilViewVariable** interface has these methods.



| Method                                                                                     | Description                                              |
|:-------------------------------------------------------------------------------------------|:---------------------------------------------------------|
| [**GetDepthStencil**](./id3dx11effectdepthstencilviewvariable-getdepthstencil-92e610e6a2.md)           | Get a depth-stencil-view resource.<br/>            |
| [**GetDepthStencilArray**](./id3dx11effectdepthstencilviewvariable-getdepthstencilarray-29015f8145.md) | Get an array of depth-stencil-view resources.<br/> |
| [**SetDepthStencil**](./id3dx11effectdepthstencilviewvariable-setdepthstencil-d7e599c397.md)           | Set a depth-stencil-view resource.<br/>            |
| [**SetDepthStencilArray**](./id3dx11effectdepthstencilviewvariable-setdepthstencilarray-3ac91ac5ac.md) | Set an array of depth-stencil-view resources.<br/> |



 

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

[**ID3DX11EffectVariable**](./id3dx11effectvariable-89fd46cf57.md)
</dt> <dt>

[Effects 11 Interfaces](./d3d11-graphics-reference-effects11-interfaces-5b7b91a9df.md)
</dt> <dt>

[D3DX Interfaces](./d3d11-graphics-reference-d3dx11-interfaces-bf8653ed03.md)
</dt> </dl>