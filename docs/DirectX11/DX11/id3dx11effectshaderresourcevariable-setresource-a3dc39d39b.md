Source: [https://learn.microsoft.com/en-us/windows/win32/direct3d11/id3dx11effectshaderresourcevariable-setresource](<https://learn.microsoft.com/en-us/windows/win32/direct3d11/id3dx11effectshaderresourcevariable-setresource>)

# ID3DX11EffectShaderResourceVariable::SetResource method

Set a shader resource.

## Syntax


```C++
HRESULT SetResource(
   ID3D11ShaderResourceView *pResource
);
```



## Parameters

<dl> <dt>

*pResource* 
</dt> <dd>

Type: **[**ID3D11ShaderResourceView**](./nn-d3d11-id3d11shaderresourceview-e26d3e0c03.md)\***

The address of a pointer to a shader-resource-view interface. See [**ID3D11ShaderResourceView**](./nn-d3d11-id3d11shaderresourceview-e26d3e0c03.md).

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

[ID3DX11EffectShaderResourceVariable](./id3dx11effectshaderresourcevariable-d5157ae671.md)
</dt> </dl>