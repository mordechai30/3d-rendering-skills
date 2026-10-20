Source: [https://learn.microsoft.com/en-us/windows/win32/direct3d11/id3dx11effectscalarvariable](<https://learn.microsoft.com/en-us/windows/win32/direct3d11/id3dx11effectscalarvariable>)

# ID3DX11EffectScalarVariable interface

An effect-scalar-variable interface accesses scalar values.

## Members

The **ID3DX11EffectScalarVariable** interface inherits from [**ID3DX11EffectVariable**](./id3dx11effectvariable-89fd46cf57.md). **ID3DX11EffectScalarVariable** also has these types of members:

-   [Methods](#methods)

### Methods

The **ID3DX11EffectScalarVariable** interface has these methods.



| Method                                                             | Description                                          |
|:-------------------------------------------------------------------|:-----------------------------------------------------|
| [**GetBool**](./id3dx11effectscalarvariable-getbool-301ab3519e.md)             | Get a boolean variable.<br/>                   |
| [**GetBoolArray**](./id3dx11effectscalarvariable-getboolarray-7c5c77e3e7.md)   | Get an array of boolean variables.<br/>        |
| [**GetFloat**](./id3dx11effectscalarvariable-getfloat-bba7c4ed8d.md)           | Get a floating-point variable.<br/>            |
| [**GetFloatArray**](./id3dx11effectscalarvariable-getfloatarray-543d6f16cb.md) | Get an array of floating-point variables.<br/> |
| [**GetInt**](./id3dx11effectscalarvariable-getint-7bb6261538.md)               | Get an integer variable.<br/>                  |
| [**GetIntArray**](./id3dx11effectscalarvariable-getintarray-c51c7f895c.md)     | Get an array of integer variables.<br/>        |
| [**SetBool**](./id3dx11effectscalarvariable-setbool-b7c6062668.md)             | Set a boolean variable.<br/>                   |
| [**SetBoolArray**](./id3dx11effectscalarvariable-setboolarray-3a1dfd8822.md)   | Set an array of boolean variables.<br/>        |
| [**SetFloat**](./id3dx11effectscalarvariable-setfloat-a208e1b385.md)           | Set a floating-point variable.<br/>            |
| [**SetFloatArray**](./id3dx11effectscalarvariable-setfloatarray-d9ecde9364.md) | Set an array of floating-point variables.<br/> |
| [**SetInt**](./id3dx11effectscalarvariable-setint-b37659ebf8.md)               | Set an integer variable.<br/>                  |
| [**SetIntArray**](./id3dx11effectscalarvariable-setintarray-bc980e560a.md)     | Set an array of integer variables.<br/>        |



 

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