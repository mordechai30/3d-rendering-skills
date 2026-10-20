Source: [https://learn.microsoft.com/en-us/windows/win32/direct3d11/id3dx11effectsamplervariable-getsampler](<https://learn.microsoft.com/en-us/windows/win32/direct3d11/id3dx11effectsamplervariable-getsampler>)

# ID3DX11EffectSamplerVariable::GetSampler method

Get a pointer to a sampler interface.

## Syntax


```C++
HRESULT GetSampler(
   UINT               Index,
   ID3D11SamplerState **ppSampler
);
```



## Parameters

<dl> <dt>

*Index* 
</dt> <dd>

Type: **[**UINT**](/windows/desktop/WinProg/windows-data-types)**

Index into an array of sampler interfaces. If there is only one sampler interface, use 0.

</dd> <dt>

*ppSampler* 
</dt> <dd>

Type: **[**ID3D11SamplerState**](./nn-d3d11-id3d11samplerstate-f4d3826030.md)\*\***

The address of a pointer to a sampler interface (see [**ID3D11SamplerState**](./nn-d3d11-id3d11samplerstate-f4d3826030.md)).

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