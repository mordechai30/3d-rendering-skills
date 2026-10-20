Source: [https://learn.microsoft.com/en-us/windows/win32/direct3d11/id3dx11effectshadervariable-getinputsignatureelementdesc](<https://learn.microsoft.com/en-us/windows/win32/direct3d11/id3dx11effectshadervariable-getinputsignatureelementdesc>)

# ID3DX11EffectShaderVariable::GetInputSignatureElementDesc method

Get an input-signature description.

## Syntax


```C++
HRESULT GetInputSignatureElementDesc(
   UINT                           ShaderIndex,
   UINT                           Element,
   D3D11_SIGNATURE_PARAMETER_DESC *pDesc
);
```



## Parameters

<dl> <dt>

*ShaderIndex* 
</dt> <dd>

Type: **[**UINT**](/windows/desktop/WinProg/windows-data-types)**

A zero-based shader index.

</dd> <dt>

*Element* 
</dt> <dd>

Type: **[**UINT**](/windows/desktop/WinProg/windows-data-types)**

A zero-based shader-element index.

</dd> <dt>

*pDesc* 
</dt> <dd>

Type: **[**D3D11\_SIGNATURE\_PARAMETER\_DESC**](./ns-d3d11shader-d3d11_signature_parameter_desc-0edc1becc0.md)\***

A pointer to a parameter description (see [**D3D11\_SIGNATURE\_PARAMETER\_DESC**](./ns-d3d11shader-d3d11_signature_parameter_desc-0edc1becc0.md)).

</dd> </dl>

## Return value

Type: **[**HRESULT**](https://msdn.microsoft.com/library/Bb401631(v=MSDN.10).aspx)**

Returns one of the following [Direct3D 11 Return Codes](./d3d11-graphics-reference-returnvalues-2d2638a6a7.md).

## Remarks

An effect contains one or more shaders; each shader has an input and output signature; each signature contains one or more elements (or parameters). The shader index identifies the shader and the element index identifies the element (or parameter) in the shader signature.

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