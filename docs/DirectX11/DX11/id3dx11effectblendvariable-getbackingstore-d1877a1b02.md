Source: [https://learn.microsoft.com/en-us/windows/win32/direct3d11/id3dx11effectblendvariable-getbackingstore](<https://learn.microsoft.com/en-us/windows/win32/direct3d11/id3dx11effectblendvariable-getbackingstore>)

# ID3DX11EffectBlendVariable::GetBackingStore method

Get a pointer to a blend-state variable.

## Syntax


```C++
HRESULT GetBackingStore(
   UINT             Index,
   D3D11_BLEND_DESC *pBlendDesc
);
```



## Parameters

<dl> <dt>

*Index* 
</dt> <dd>

Type: **[**UINT**](/windows/desktop/WinProg/windows-data-types)**

Index into an array of blend-state descriptions. If there is only one blend-state variable in the effect, use 0.

</dd> <dt>

*pBlendDesc* 
</dt> <dd>

Type: **[**D3D11\_BLEND\_DESC**](./ns-d3d11-d3d11_blend_desc-dbb11ca57b.md)\***

A pointer to a blend-state description (see [**D3D11\_BLEND\_DESC**](./ns-d3d11-d3d11_blend_desc-dbb11ca57b.md)).

</dd> </dl>

## Return value

Type: **[**HRESULT**](https://msdn.microsoft.com/library/Bb401631(v=MSDN.10).aspx)**

Returns one of the following [Direct3D 11 Return Codes](./d3d11-graphics-reference-returnvalues-2d2638a6a7.md).

## Remarks

Effect variables are saved in memory in the backing store; when a technique is applied, the values in the backing store are copied to the device. Backing store data can used to recreate the variable when necessary.

> [!Note]  
> The DirectX SDK does not supply any compiled binaries for effects. You must use Effects 11 source to build your effects-type application. For more information about using Effects 11 source, see [Differences Between Effects 10 and Effects 11](./d3d11-graphics-programming-guide-effects-differences-f7025c8c69.md).

 

## Requirements



| Requirement | Value |
|--------------------|----------------------------------------------------------------------------------------------------------------------------------------------|
| Header<br/>  | <dl> <dt>D3dx11effect.h</dt> </dl>                                                    |
| Library<br/> | <dl> <dt>N/A (An Effects 11 library is available online as shared source.)</dt> </dl> |



## See also

<dl> <dt>

[ID3DX11EffectBlendVariable](./id3dx11effectblendvariable-1cac3f92ff.md)
</dt> </dl>