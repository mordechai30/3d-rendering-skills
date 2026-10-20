Source: [https://learn.microsoft.com/en-us/windows/win32/direct3d11/id3dx11effectconstantbuffer](<https://learn.microsoft.com/en-us/windows/win32/direct3d11/id3dx11effectconstantbuffer>)

# ID3DX11EffectConstantBuffer interface

A constant-buffer interface accesses constant buffers or texture buffers.

## Members

The **ID3DX11EffectConstantBuffer** interface inherits from [**ID3DX11EffectVariable**](./id3dx11effectvariable-89fd46cf57.md). **ID3DX11EffectConstantBuffer** also has these types of members:

-   [Methods](#methods)

### Methods

The **ID3DX11EffectConstantBuffer** interface has these methods.



| Method                                                                             | Description                                          |
|:-----------------------------------------------------------------------------------|:-----------------------------------------------------|
| [**GetConstantBuffer**](./id3dx11effectconstantbuffer-getconstantbuffer-e1a26a3a0c.md)         | Get a constant-buffer.<br/>                    |
| [**GetTextureBuffer**](./id3dx11effectconstantbuffer-gettexturebuffer-d1d3bb526b.md)           | Get a texture-buffer.<br/>                     |
| [**SetConstantBuffer**](./id3dx11effectconstantbuffer-setconstantbuffer-6b4bc55e0b.md)         | Set a constant-buffer.<br/>                    |
| [**SetTextureBuffer**](./id3dx11effectconstantbuffer-settexturebuffer-a9a88e5352.md)           | Set a texture-buffer.<br/>                     |
| [**UndoSetConstantBuffer**](./id3dx11effectconstantbuffer-undosetconstantbuffer-e64cb68e09.md) | Reverts a previously set constant buffer.<br/> |
| [**UndoSetTextureBuffer**](./id3dx11effectconstantbuffer-undosettexturebuffer-d5efb1a09d.md)   | Reverts a previously set texture buffer.<br/>  |



 

## Remarks

Use constant buffers to store many effect constants; grouping constants into buffers based on their frequency of update. This allows you to minimize the number of state changes as well as make the fewest API calls to change state. Both of these factors lead to better performance.

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