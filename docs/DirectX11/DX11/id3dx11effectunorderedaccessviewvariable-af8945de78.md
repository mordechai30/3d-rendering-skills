Source: [https://learn.microsoft.com/en-us/windows/win32/direct3d11/id3dx11effectunorderedaccessviewvariable](<https://learn.microsoft.com/en-us/windows/win32/direct3d11/id3dx11effectunorderedaccessviewvariable>)

# ID3DX11EffectUnorderedAccessViewVariable interface

Accesses an unordered access view.

## Members

The **ID3DX11EffectUnorderedAccessViewVariable** interface inherits from [**ID3DX11EffectVariable**](./id3dx11effectvariable-89fd46cf57.md). **ID3DX11EffectUnorderedAccessViewVariable** also has these types of members:

-   [Methods](#methods)

### Methods

The **ID3DX11EffectUnorderedAccessViewVariable** interface has these methods.



| Method                                                                                                      | Description                                        |
|:------------------------------------------------------------------------------------------------------------|:---------------------------------------------------|
| [**GetUnorderedAccessView**](./id3dx11effectunorderedaccessviewvariable-getunorderedaccessview-c37b898500.md)           | Get an unordered-access-view.<br/>           |
| [**GetUnorderedAccessViewArray**](./id3dx11effectunorderedaccessviewvariable-getunorderedaccessviewarray-e5e4b405f1.md) | Get an array of unordered-access-views.<br/> |
| [**SetUnorderedAccessView**](./id3dx11effectunorderedaccessviewvariable-setunorderedaccessview-23e9b4171b.md)           | Set an unordered-access-view.<br/>           |
| [**SetUnorderedAccessViewArray**](./id3dx11effectunorderedaccessviewvariable-setunorderedaccessviewarray-9672cceb92.md) | Set an array of unordered-access-views.<br/> |



 

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