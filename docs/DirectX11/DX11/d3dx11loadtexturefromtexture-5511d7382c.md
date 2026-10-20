Source: [https://learn.microsoft.com/en-us/windows/win32/direct3d11/d3dx11loadtexturefromtexture](<https://learn.microsoft.com/en-us/windows/win32/direct3d11/d3dx11loadtexturefromtexture>)

# D3DX11LoadTextureFromTexture function

> [!Note]  
> The D3DX (D3DX 9, D3DX 10, and D3DX 11) utility library is deprecated for Windows 8 and is not supported for Windows Store apps.

 

> [!Note]  
> Instead of using this function, we recommend that you use the [DirectXTex](https://github.com/Microsoft/DirectXTex) library, **Resize**, **Convert**, **Compress**, **Decompress**, and/or **CopyRectangle**.

 

Load a texture from a texture.

## Syntax


```C++
HRESULT D3DX11LoadTextureFromTexture(
   ID3D11DeviceContext      *pContext,
   ID3D11Resource           *pSrcTexture,
   D3DX11_TEXTURE_LOAD_INFO *pLoadInfo,
   ID3D11Resource           *pDstTexture
);
```



## Parameters

<dl> <dt>

*pContext* 
</dt> <dd>

Type: **[**ID3D11DeviceContext**](./nn-d3d11-id3d11devicecontext-abe911f651.md)\***

A pointer to an [**ID3D11DeviceContext**](./nn-d3d11-id3d11devicecontext-abe911f651.md) object.

</dd> <dt>

*pSrcTexture* 
</dt> <dd>

Type: **[**ID3D11Resource**](./nn-d3d11-id3d11resource-87288ccb83.md)\***

Pointer to the source texture. See [**ID3D11Resource**](./nn-d3d11-id3d11resource-87288ccb83.md).

</dd> <dt>

*pLoadInfo* 
</dt> <dd>

Type: **[**D3DX11\_TEXTURE\_LOAD\_INFO**](./d3dx11-texture-load-info-9577b114e1.md)\***

Pointer to texture loading parameters. See [**D3DX11\_TEXTURE\_LOAD\_INFO**](./d3dx11-texture-load-info-9577b114e1.md).

</dd> <dt>

*pDstTexture* 
</dt> <dd>

Type: **[**ID3D11Resource**](./nn-d3d11-id3d11resource-87288ccb83.md)\***

Pointer to the destination texture. See [**ID3D11Resource**](./nn-d3d11-id3d11resource-87288ccb83.md).

</dd> </dl>

## Return value

Type: **[**HRESULT**](https://msdn.microsoft.com/library/Bb401631(v=MSDN.10).aspx)**

The return value is one of the values listed in [Direct3D 11 Return Codes](./d3d11-graphics-reference-returnvalues-2d2638a6a7.md).

## Requirements



| Requirement | Value |
|--------------------|----------------------------------------------------------------------------------------|
| Header<br/>  | <dl> <dt>D3DX11tex.h</dt> </dl> |
| Library<br/> | <dl> <dt>D3DX11.lib</dt> </dl>  |



## See also

<dl> <dt>

[D3DX Functions](./d3d11-graphics-reference-d3dx11-functions-e9c2bae664.md)
</dt> </dl>