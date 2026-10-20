Source: [https://learn.microsoft.com/en-us/windows/win32/direct3d11/id3dx11effectmatrixvariable](<https://learn.microsoft.com/en-us/windows/win32/direct3d11/id3dx11effectmatrixvariable>)

# ID3DX11EffectMatrixVariable interface

A matrix-variable interface accesses a matrix.

## Members

The **ID3DX11EffectMatrixVariable** interface inherits from [**ID3DX11EffectVariable**](./id3dx11effectvariable-89fd46cf57.md). **ID3DX11EffectMatrixVariable** also has these types of members:

-   [Methods](#methods)

### Methods

The **ID3DX11EffectMatrixVariable** interface has these methods.



| Method                                                                                 | Description                                                       |
|:---------------------------------------------------------------------------------------|:------------------------------------------------------------------|
| [**GetMatrix**](./id3dx11effectmatrixvariable-getmatrix-983bede3c7.md)                             | Get a matrix.<br/>                                          |
| [**GetMatrixArray**](./id3dx11effectmatrixvariable-getmatrixarray-88c1b32c97.md)                   | Get an array of matrices.<br/>                              |
| [**GetMatrixTranspose**](./id3dx11effectmatrixvariable-getmatrixtranspose-e637ca2119.md)           | Transpose and get a floating-point matrix.<br/>             |
| [**GetMatrixTransposeArray**](./id3dx11effectmatrixvariable-getmatrixtransposearray-1da4907090.md) | Transpose and get an array of floating-point matrices.<br/> |
| [**SetMatrix**](./id3dx11effectmatrixvariable-setmatrix-9310b4ed24.md)                             | Set a floating-point matrix.<br/>                           |
| [**SetMatrixArray**](./id3dx11effectmatrixvariable-setmatrixarray-e0b5880a0c.md)                   | Set an array of floating-point matrices.<br/>               |
| [**SetMatrixTranspose**](./id3dx11effectmatrixvariable-setmatrixtranspose-947455e34c.md)           | Transpose and set a floating-point matrix.<br/>             |
| [**SetMatrixTransposeArray**](./id3dx11effectmatrixvariable-setmatrixtransposearray-a29b82b2e7.md) | Transpose and set an array of floating-point matrices.<br/> |



 

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