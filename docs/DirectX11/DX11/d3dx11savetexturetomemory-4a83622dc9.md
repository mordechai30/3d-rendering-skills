Source: [https://learn.microsoft.com/en-us/windows/win32/direct3d11/d3dx11savetexturetomemory](<https://learn.microsoft.com/en-us/windows/win32/direct3d11/d3dx11savetexturetomemory>)

# D3DX11SaveTextureToMemory function

> [!Note]  
> The D3DX (D3DX 9, D3DX 10, and D3DX 11) utility library is deprecated for Windows 8 and is not supported for Windows Store apps.

 

> [!Note]  
> Instead of using this function, we recommend that you use the [DirectXTex](https://github.com/Microsoft/DirectXTex) library, **CaptureTexture** then **SaveToXXXMemory** (where XXX is WIC, DDS, or TGA; WIC doesn't support DDS and TGA; D3DX 9 supported TGA as a common art source format for games).

 

Save a texture to memory.

## Syntax


```C++
HRESULT D3DX11SaveTextureToMemory(
        ID3D11DeviceContext      *pContext,
  _In_  ID3D11Resource           *pSrcTexture,
  _In_  D3DX11_IMAGE_FILE_FORMAT DestFormat,
  _Out_ LPD3D10BLOB              *ppDestBuf,
  _In_  UINT                     Flags
);
```



## Parameters

<dl> <dt>

*pContext* 
</dt> <dd>

Type: **[**ID3D11DeviceContext**](./nn-d3d11-id3d11devicecontext-abe911f651.md)\***

A pointer to an [**ID3D11DeviceContext**](./nn-d3d11-id3d11devicecontext-abe911f651.md) object.

</dd> <dt>

*pSrcTexture* \[in\]
</dt> <dd>

Type: **[**ID3D11Resource**](./nn-d3d11-id3d11resource-87288ccb83.md)\***

Pointer to the texture to be saved. See [**ID3D11Resource**](./nn-d3d11-id3d11resource-87288ccb83.md).

</dd> <dt>

*DestFormat* \[in\]
</dt> <dd>

Type: **[**D3DX11\_IMAGE\_FILE\_FORMAT**](./d3dx11-image-file-format-77284c5dc9.md)**

The format the texture will be saved as. See [**D3DX11\_IMAGE\_FILE\_FORMAT**](./d3dx11-image-file-format-77284c5dc9.md).

</dd> <dt>

*ppDestBuf* \[out\]
</dt> <dd>

Type: **[**LPD3D10BLOB**](./nn-d3dcommon-id3d10blob-6eb12d2a9d.md)\***

Address of a pointer to the memory containing the saved texture.

</dd> <dt>

*Flags* \[in\]
</dt> <dd>

Type: **[**UINT**](/windows/desktop/WinProg/windows-data-types)**

Optional.

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