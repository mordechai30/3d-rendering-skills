Source: [https://learn.microsoft.com/en-us/windows/win32/direct3d11/id3dx11effectblendvariable](<https://learn.microsoft.com/en-us/windows/win32/direct3d11/id3dx11effectblendvariable>)

# ID3DX11EffectBlendVariable interface

The blend-variable interface accesses blend state.

## Members

The **ID3DX11EffectBlendVariable** interface inherits from [**ID3DX11EffectVariable**](./id3dx11effectvariable-89fd46cf57.md). **ID3DX11EffectBlendVariable** also has these types of members:

-   [Methods](#methods)

### Methods

The **ID3DX11EffectBlendVariable** interface has these methods.



| Method                                                                    | Description                                          |
|:--------------------------------------------------------------------------|:-----------------------------------------------------|
| [**GetBackingStore**](./id3dx11effectblendvariable-getbackingstore-d1877a1b02.md)     | Get a pointer to a blend-state variable.<br/>  |
| [**GetBlendState**](./id3dx11effectblendvariable-getblendstate-1c30f218fd.md)         | Get a pointer to a blend-state interface.<br/> |
| [**SetBlendState**](./id3dx11effectblendvariable-setblendstate-4445f29ffc.md)         | Sets an effect's blend-state.<br/>             |
| [**UndoSetBlendState**](./id3dx11effectblendvariable-undosetblendstate-1c4208ed6e.md) | Reverts a previously set blend-state.<br/>     |



 

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