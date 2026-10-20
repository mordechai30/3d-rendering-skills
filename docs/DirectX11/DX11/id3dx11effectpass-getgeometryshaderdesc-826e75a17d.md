Source: [https://learn.microsoft.com/en-us/windows/win32/direct3d11/id3dx11effectpass-getgeometryshaderdesc](<https://learn.microsoft.com/en-us/windows/win32/direct3d11/id3dx11effectpass-getgeometryshaderdesc>)

# ID3DX11EffectPass::GetGeometryShaderDesc method

Get a geometry-shader description.

## Syntax


```C++
HRESULT GetGeometryShaderDesc(
   D3DX11_PASS_SHADER_DESC *pDesc
);
```



## Parameters

<dl> <dt>

*pDesc* 
</dt> <dd>

Type: **[**D3DX11\_PASS\_SHADER\_DESC**](./d3dx11-pass-shader-desc-1681b12e9f.md)\***

A pointer to a geometry-shader description (see [**D3DX11\_PASS\_SHADER\_DESC**](./d3dx11-pass-shader-desc-1681b12e9f.md)).

</dd> </dl>

## Return value

Type: **[**HRESULT**](https://msdn.microsoft.com/library/Bb401631(v=MSDN.10).aspx)**

Returns one of the following [Direct3D 11 Return Codes](./d3d11-graphics-reference-returnvalues-2d2638a6a7.md).

## Remarks

An effect pass can contain render state assignments and shader object assignments.

> [!Note]  
> The DirectX SDK does not supply any compiled binaries for effects. You must use Effects 11 source to build your effects-type application. For more information about using Effects 11 source, see [Differences Between Effects 10 and Effects 11](./d3d11-graphics-programming-guide-effects-differences-f7025c8c69.md).

 

## Requirements



| Requirement | Value |
|--------------------|----------------------------------------------------------------------------------------------------------------------------------------------|
| Header<br/>  | <dl> <dt>D3dx11effect.h</dt> </dl>                                                    |
| Library<br/> | <dl> <dt>N/A (An Effects 11 library is available online as shared source.)</dt> </dl> |



## See also

<dl> <dt>

[ID3DX11EffectPass](./id3dx11effectpass-6c2d5d6dfa.md)
</dt> </dl>