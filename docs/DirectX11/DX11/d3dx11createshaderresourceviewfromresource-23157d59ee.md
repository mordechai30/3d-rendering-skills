Source: [https://learn.microsoft.com/en-us/windows/win32/direct3d11/d3dx11createshaderresourceviewfromresource](<https://learn.microsoft.com/en-us/windows/win32/direct3d11/d3dx11createshaderresourceviewfromresource>)

# D3DX11CreateShaderResourceViewFromResource function

> [!Note]  
> The D3DX (D3DX 9, D3DX 10, and D3DX 11) utility library is deprecated for Windows 8 and is not supported for Windows Store apps.

 

> [!Note]  
> Instead of using this function, we recommend that you use [resource functions](/windows/desktop/menurc/resources-functions), then these:
>
> -   [DirectXTK](https://github.com/Microsoft/DirectXTK) library (runtime), **CreateXXXTextureFromMemory** (where XXX is DDS or WIC)
> -   [DirectXTex](https://github.com/Microsoft/DirectXTex) library (tools), **LoadFromXXXMemory** (where XXX is WIC, DDS, or TGA; WIC doesn't support DDS and TGA; D3DX 9 supported TGA as a common art source format for games) then **CreateShaderResourceView**

 

Create a shader-resource view from a resource.

## Syntax


```C++
HRESULT D3DX11CreateShaderResourceViewFromResource(
  _In_  ID3D11Device             *pDevice,
  _In_  HMODULE                  hSrcModule,
  _In_  LPCTSTR                  pSrcResource,
  _In_  D3DX11_IMAGE_LOAD_INFO   *pLoadInfo,
  _In_  ID3DX11ThreadPump        *pPump,
  _Out_ ID3D11ShaderResourceView **ppShaderResourceView,
  _Out_ HRESULT                  *pHResult
);
```



## Parameters

<dl> <dt>

*pDevice* \[in\]
</dt> <dd>

Type: **[**ID3D11Device**](./nn-d3d11-id3d11device-6e49ef4b9e.md)\***

A pointer to the device (see [**ID3D11Device**](./nn-d3d11-id3d11device-6e49ef4b9e.md)) that will use the resource.

</dd> <dt>

*hSrcModule* \[in\]
</dt> <dd>

Type: **[**HMODULE**](/windows/desktop/WinProg/windows-data-types)**

Handle to the resource module containing the shader-resource view. HMODULE can be obtained with [GetModuleHandle Function](/windows/desktop/api/libloaderapi/nf-libloaderapi-getmodulehandlea).

</dd> <dt>

*pSrcResource* \[in\]
</dt> <dd>

Type: **[**LPCTSTR**](/windows/desktop/WinProg/windows-data-types)**

Name of the shader resource view in hSrcModule. If the compiler settings require Unicode, the data type LPCTSTR resolves to LPCWSTR. Otherwise, the data type resolves to LPCSTR.

</dd> <dt>

*pLoadInfo* \[in\]
</dt> <dd>

Type: **[**D3DX11\_IMAGE\_LOAD\_INFO**](./d3dx11-image-load-info-f25c3d92f3.md)\***

Optional. Identifies the characteristics of a texture (see [**D3DX11\_IMAGE\_LOAD\_INFO**](./d3dx11-image-load-info-f25c3d92f3.md)) when the data processor is created; set this to **NULL** to read the characteristics of a texture when the texture is loaded.

</dd> <dt>

*pPump* \[in\]
</dt> <dd>

Type: **[**ID3DX11ThreadPump**](./id3dx11threadpump-1d47459670.md)\***

A pointer to a thread pump interface (see [**ID3DX11ThreadPump Interface**](./id3dx11threadpump-1d47459670.md)). If **NULL** is specified, this function will behave synchronously and will not return until it is finished.

</dd> <dt>

*ppShaderResourceView* \[out\]
</dt> <dd>

Type: **[**ID3D11ShaderResourceView**](./nn-d3d11-id3d11shaderresourceview-e26d3e0c03.md)\*\***

Address of a pointer to the shader-resource view (see [**ID3D11ShaderResourceView**](./nn-d3d11-id3d11shaderresourceview-e26d3e0c03.md)).

</dd> <dt>

*pHResult* \[out\]
</dt> <dd>

Type: **[**HRESULT**](https://msdn.microsoft.com/library/Bb401631(v=MSDN.10).aspx)\***

A pointer to the return value. May be **NULL**. If *pPump* is not **NULL**, then *pHResult* must be a valid memory location until the asynchronous execution completes.

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