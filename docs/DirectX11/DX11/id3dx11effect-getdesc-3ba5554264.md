Source: [https://learn.microsoft.com/en-us/windows/win32/direct3d11/id3dx11effect-getdesc](<https://learn.microsoft.com/en-us/windows/win32/direct3d11/id3dx11effect-getdesc>)

# ID3DX11Effect::GetDesc method

Get an effect description.

## Syntax


```C++
HRESULT GetDesc(
   D3DX11_EFFECT_DESC *pDesc
);
```



## Parameters

<dl> <dt>

*pDesc* 
</dt> <dd>

Type: **[**D3DX11\_EFFECT\_DESC**](./d3dx11-effect-desc-95d47e21fd.md)\***

A pointer to an effect description (see [**D3DX11\_EFFECT\_DESC**](./d3dx11-effect-desc-95d47e21fd.md)).

</dd> </dl>

## Return value

Type: **[**HRESULT**](https://msdn.microsoft.com/library/Bb401631(v=MSDN.10).aspx)**

Returns one of the following [Direct3D 11 Return Codes](./d3d11-graphics-reference-returnvalues-2d2638a6a7.md).

## Remarks

An effect description contains basic information about an effect such as the techniques it contains and the constant buffer resources it requires.

> [!Note]  
> The DirectX SDK does not supply any compiled binaries for effects. You must use Effects 11 source to build your effects-type application. For more information about using Effects 11 source, see [Differences Between Effects 10 and Effects 11](./d3d11-graphics-programming-guide-effects-differences-f7025c8c69.md).

 

## Requirements



| Requirement | Value |
|--------------------|----------------------------------------------------------------------------------------------------------------------------------------------|
| Header<br/>  | <dl> <dt>D3dx11effect.h</dt> </dl>                                                    |
| Library<br/> | <dl> <dt>N/A (An Effects 11 library is available online as shared source.)</dt> </dl> |



## See also

<dl> <dt>

[ID3DX11Effect](./id3dx11effect-277b450b03.md)
</dt> </dl>