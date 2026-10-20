Source: [https://learn.microsoft.com/en-us/windows/win32/direct3d11/id3dx11effecttype-getdesc](<https://learn.microsoft.com/en-us/windows/win32/direct3d11/id3dx11effecttype-getdesc>)

# ID3DX11EffectType::GetDesc method

Get an effect-type description.

## Syntax


```C++
HRESULT GetDesc(
   D3DX11_EFFECT_TYPE_DESC *pDesc
);
```



## Parameters

<dl> <dt>

*pDesc* 
</dt> <dd>

Type: **[**D3DX11\_EFFECT\_TYPE\_DESC**](./d3dx11-effect-type-desc-425f26f5bb.md)\***

A pointer to an effect-type description. See [**D3DX11\_EFFECT\_TYPE\_DESC**](./d3dx11-effect-type-desc-425f26f5bb.md).

</dd> </dl>

## Return value

Type: **[**HRESULT**](https://msdn.microsoft.com/library/Bb401631(v=MSDN.10).aspx)**

Returns one of the following [Direct3D 11 Return Codes](./d3d11-graphics-reference-returnvalues-2d2638a6a7.md).

## Remarks

The effect-variable description contains data about the name, annotations, semantic, flags and buffer offset of the effect type.

> [!Note]  
> The DirectX SDK does not supply any compiled binaries for effects. You must use Effects 11 source to build your effects-type application. For more information about using Effects 11 source, see [Differences Between Effects 10 and Effects 11](./d3d11-graphics-programming-guide-effects-differences-f7025c8c69.md).

 

## Requirements



| Requirement | Value |
|--------------------|----------------------------------------------------------------------------------------------------------------------------------------------|
| Header<br/>  | <dl> <dt>D3dx11effect.h</dt> </dl>                                                    |
| Library<br/> | <dl> <dt>N/A (An Effects 11 library is available online as shared source.)</dt> </dl> |



## See also

<dl> <dt>

[ID3DX11EffectType](./id3dx11effecttype-fd26b9b277.md)
</dt> </dl>