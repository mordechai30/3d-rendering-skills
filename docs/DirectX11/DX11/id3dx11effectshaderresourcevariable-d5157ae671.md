Source: [https://learn.microsoft.com/en-us/windows/win32/direct3d11/id3dx11effectshaderresourcevariable](<https://learn.microsoft.com/en-us/windows/win32/direct3d11/id3dx11effectshaderresourcevariable>)

# ID3DX11EffectShaderResourceVariable interface

A shader-resource interface accesses a shader resource.

## Members

The **ID3DX11EffectShaderResourceVariable** interface inherits from [**ID3DX11EffectVariable**](./id3dx11effectvariable-89fd46cf57.md). **ID3DX11EffectShaderResourceVariable** also has these types of members:

-   [Methods](#methods)

### Methods

The **ID3DX11EffectShaderResourceVariable** interface has these methods.



| Method                                                                           | Description                                  |
|:---------------------------------------------------------------------------------|:---------------------------------------------|
| [**GetResource**](./id3dx11effectshaderresourcevariable-getresource-ba0243c781.md)           | Get a shader resource.<br/>            |
| [**GetResourceArray**](./id3dx11effectshaderresourcevariable-getresourcearray-d53eaac28c.md) | Get an array of shader resources.<br/> |
| [**SetResource**](./id3dx11effectshaderresourcevariable-setresource-a3dc39d39b.md)           | Set a shader resource.<br/>            |
| [**SetResourceArray**](./id3dx11effectshaderresourcevariable-setresourcearray-f340867d15.md) | Set an array of shader resources.<br/> |



 

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