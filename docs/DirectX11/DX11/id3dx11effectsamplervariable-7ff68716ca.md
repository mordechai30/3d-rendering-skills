Source: [https://learn.microsoft.com/en-us/windows/win32/direct3d11/id3dx11effectsamplervariable](<https://learn.microsoft.com/en-us/windows/win32/direct3d11/id3dx11effectsamplervariable>)

# ID3DX11EffectSamplerVariable interface

A sampler interface accesses sampler state.

## Members

The **ID3DX11EffectSamplerVariable** interface inherits from [**ID3DX11EffectVariable**](./id3dx11effectvariable-89fd46cf57.md). **ID3DX11EffectSamplerVariable** also has these types of members:

-   [Methods](#methods)

### Methods

The **ID3DX11EffectSamplerVariable** interface has these methods.



| Method                                                                  | Description                                                         |
|:------------------------------------------------------------------------|:--------------------------------------------------------------------|
| [**GetBackingStore**](./id3dx11effectsamplervariable-getbackingstore-f39fd2b458.md) | Get a pointer to a variable that contains sampler state.<br/> |
| [**GetSampler**](./id3dx11effectsamplervariable-getsampler-8a26464b6c.md)           | Get a pointer to a sampler interface.<br/>                    |
| [**SetSampler**](./id3dx11effectsamplervariable-setsampler-02a64c3d32.md)           | Set sampler state.<br/>                                       |
| [**UndoSetSampler**](./id3dx11effectsamplervariable-undosetsampler-9e4502f89d.md)   | Revert a previously set sampler state.<br/>                   |



 

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