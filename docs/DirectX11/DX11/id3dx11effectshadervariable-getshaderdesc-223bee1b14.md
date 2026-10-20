Source: [https://learn.microsoft.com/en-us/windows/win32/direct3d11/id3dx11effectshadervariable-getshaderdesc](<https://learn.microsoft.com/en-us/windows/win32/direct3d11/id3dx11effectshadervariable-getshaderdesc>)

# ID3DX11EffectShaderVariable::GetShaderDesc method

Get a shader description.

## Syntax


```C++
HRESULT GetShaderDesc(
   UINT                      ShaderIndex,
   D3DX11_EFFECT_SHADER_DESC *pDesc
);
```



## Parameters

<dl> <dt>

*ShaderIndex* 
</dt> <dd>

Type: **[**UINT**](/windows/desktop/WinProg/windows-data-types)**

A zero-based index.

</dd> <dt>

*pDesc* 
</dt> <dd>

Type: **[**D3DX11\_EFFECT\_SHADER\_DESC**](./d3dx11-effect-shader-desc-44320d650b.md)\***

A pointer to a shader description (see [**D3DX11\_EFFECT\_SHADER\_DESC**](./d3dx11-effect-shader-desc-44320d650b.md)).

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

[ID3DX11EffectShaderVariable](./id3dx11effectshadervariable-81ab8d90dd.md)
</dt> </dl>