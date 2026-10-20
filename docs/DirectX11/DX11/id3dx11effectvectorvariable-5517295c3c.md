Source: [https://learn.microsoft.com/en-us/windows/win32/direct3d11/id3dx11effectvectorvariable](<https://learn.microsoft.com/en-us/windows/win32/direct3d11/id3dx11effectvectorvariable>)

# ID3DX11EffectVectorVariable interface

A vector-variable interface accesses a four-component vector.

## Members

The **ID3DX11EffectVectorVariable** interface inherits from [**ID3DX11EffectVariable**](./id3dx11effectvariable-89fd46cf57.md). **ID3DX11EffectVectorVariable** also has these types of members:

-   [Methods](#methods)

### Methods

The **ID3DX11EffectVectorVariable** interface has these methods.



| Method                                                                         | Description                                                                         |
|:-------------------------------------------------------------------------------|:------------------------------------------------------------------------------------|
| [**GetBoolVector**](./id3dx11effectvectorvariable-getboolvector-398c2eee55.md)             | Get a four-component vector that contains boolean data.<br/>                  |
| [**GetBoolVectorArray**](./id3dx11effectvectorvariable-getboolvectorarray-e0a436ca3b.md)   | Get an array of four-component vectors that contain boolean data.<br/>        |
| [**GetFloatVector**](./id3dx11effectvectorvariable-getfloatvector-70a72226f7.md)           | Get a four-component vector that contains floating-point data.<br/>           |
| [**GetFloatVectorArray**](./id3dx11effectvectorvariable-getfloatvectorarray-baad9865f4.md) | Get an array of four-component vectors that contain floating-point data.<br/> |
| [**GetIntVector**](./id3dx11effectvectorvariable-getintvector-59e692cc7e.md)               | Get a four-component vector that contains integer data.<br/>                  |
| [**GetIntVectorArray**](./id3dx11effectvectorvariable-getintvectorarray-5869242b15.md)     | Get an array of four-component vectors that contain integer data.<br/>        |
| [**SetBoolVector**](./id3dx11effectvectorvariable-setboolvector-f4e84cf70d.md)             | Set a four-component vector that contains boolean data.<br/>                  |
| [**SetBoolVectorArray**](./id3dx11effectvectorvariable-setboolvectorarray-8f8a2cc8cb.md)   | Set an array of four-component vectors that contain boolean data.<br/>        |
| [**SetFloatVector**](./id3dx11effectvectorvariable-setfloatvector-25413dc2c5.md)           | Set a four-component vector that contains floating-point data.<br/>           |
| [**SetFloatVectorArray**](./id3dx11effectvectorvariable-setfloatvectorarray-af8ca45133.md) | Set an array of four-component vectors that contain floating-point data.<br/> |
| [**SetIntVector**](./id3dx11effectvectorvariable-setintvector-73dfcbd508.md)               | Set a four-component vector that contains integer data.<br/>                  |
| [**SetIntVectorArray**](./id3dx11effectvectorvariable-setintvectorarray-91fa74018a.md)     | Set an array of four-component vectors that contain integer data.<br/>        |



 

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