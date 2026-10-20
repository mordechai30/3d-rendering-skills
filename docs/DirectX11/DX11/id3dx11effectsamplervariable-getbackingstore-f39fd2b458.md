Source: [https://learn.microsoft.com/en-us/windows/win32/direct3d11/id3dx11effectsamplervariable-getbackingstore](<https://learn.microsoft.com/en-us/windows/win32/direct3d11/id3dx11effectsamplervariable-getbackingstore>)

# ID3DX11EffectSamplerVariable::GetBackingStore method

Get a pointer to a variable that contains sampler state.

## Syntax


```C++
HRESULT GetBackingStore(
   UINT               Index,
   D3D11_SAMPLER_DESC *pSamplerDesc
);
```



## Parameters

<dl> <dt>

*Index* 
</dt> <dd>

Type: **[**UINT**](/windows/desktop/WinProg/windows-data-types)**

Index into an array of sampler descriptions. If there is only one sampler variable in the effect, use 0.

</dd> <dt>

*pSamplerDesc* 
</dt> <dd>

Type: **[**D3D11\_SAMPLER\_DESC**](./ns-d3d11-d3d11_sampler_desc-f05d3e5368.md)\***

A pointer to a sampler description (see [**D3D11\_SAMPLER\_DESC**](./ns-d3d11-d3d11_sampler_desc-f05d3e5368.md)).

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

[ID3DX11EffectSamplerVariable](./id3dx11effectsamplervariable-7ff68716ca.md)
</dt> </dl>