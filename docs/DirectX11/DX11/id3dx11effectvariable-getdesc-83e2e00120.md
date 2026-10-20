Source: [https://learn.microsoft.com/en-us/windows/win32/direct3d11/id3dx11effectvariable-getdesc](<https://learn.microsoft.com/en-us/windows/win32/direct3d11/id3dx11effectvariable-getdesc>)

# ID3DX11EffectVariable::GetDesc method

Get a description.

## Syntax


```C++
HRESULT GetDesc(
   D3DX11_EFFECT_VARIABLE_DESC *pDesc
);
```



## Parameters

<dl> <dt>

*pDesc* 
</dt> <dd>

Type: **[**D3DX11\_EFFECT\_VARIABLE\_DESC**](./d3dx11-effect-variable-desc-4c62475fa5.md)\***

A pointer to an effect-variable description (see [**D3DX11\_EFFECT\_VARIABLE\_DESC**](./d3dx11-effect-variable-desc-4c62475fa5.md)).

</dd> </dl>

## Return value

Type: **[**HRESULT**](https://msdn.microsoft.com/library/Bb401631(v=MSDN.10).aspx)**

Returns one of the following [Direct3D 11 Return Codes](./d3d11-graphics-reference-returnvalues-2d2638a6a7.md).

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

[ID3DX11EffectVariable](./id3dx11effectvariable-89fd46cf57.md)
</dt> </dl>