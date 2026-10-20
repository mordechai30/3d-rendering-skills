Source: [https://learn.microsoft.com/en-us/windows/win32/direct3d11/id3dx11effectdepthstencilvariable](<https://learn.microsoft.com/en-us/windows/win32/direct3d11/id3dx11effectdepthstencilvariable>)

# ID3DX11EffectDepthStencilVariable interface

A depth-stencil-variable interface accesses depth-stencil state.

## Members

The **ID3DX11EffectDepthStencilVariable** interface inherits from [**ID3DX11EffectVariable**](./id3dx11effectvariable-89fd46cf57.md). **ID3DX11EffectDepthStencilVariable** also has these types of members:

-   [Methods](#methods)

### Methods

The **ID3DX11EffectDepthStencilVariable** interface has these methods.



| Method                                                                                         | Description                                                               |
|:-----------------------------------------------------------------------------------------------|:--------------------------------------------------------------------------|
| [**GetBackingStore**](./id3dx11effectdepthstencilvariable-getbackingstore-ddf3dd5f7e.md)                   | Get a pointer to a variable that contains depth-stencil state.<br/> |
| [**GetDepthStencilState**](./id3dx11effectdepthstencilvariable-getdepthstencilstate-280a401201.md)         | Get a pointer to a depth-stencil interface.<br/>                    |
| [**SetDepthStencilState**](./id3dx11effectdepthstencilvariable-setdepthstencilstate-4c9ae3e105.md)         | Sets the depth stencil state.<br/>                                  |
| [**UndoSetDepthStencilState**](./id3dx11effectdepthstencilvariable-undosetdepthstencilstate-67e9f488f9.md) | Reverts a previously set depth stencil state.<br/>                  |



 

## Remarks

An [**ID3DX11EffectVariable**](./id3dx11effectvariable-89fd46cf57.md) interface is created when an effect is read into memory.

Effect variables are saved in memory in the backing store; when a technique is applied, the values in the backing store are copied to the device. You can use either of these methods to return state.

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