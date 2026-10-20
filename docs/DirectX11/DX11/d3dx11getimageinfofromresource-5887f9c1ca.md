Source: [https://learn.microsoft.com/en-us/windows/win32/direct3d11/d3dx11getimageinfofromresource](<https://learn.microsoft.com/en-us/windows/win32/direct3d11/d3dx11getimageinfofromresource>)

# D3DX11GetImageInfoFromResource function

> [!Note]  
> The D3DX (D3DX 9, D3DX 10, and D3DX 11) utility library is deprecated for Windows 8 and is not supported for Windows Store apps.

 

> [!Note]  
> Instead of using this function, we recommend that you use [resource functions](/windows/desktop/menurc/resources-functions), then use [DirectXTex](https://github.com/Microsoft/DirectXTex) library (tools), **LoadFromXXXMemory** (where XXX is WIC, DDS, or TGA; WIC doesn't support DDS and TGA; D3DX 9 supported TGA as a common art source format for games).

 

Retrieves information about a given image in a resource.

## Syntax


```C++
HRESULT D3DX11GetImageInfoFromResource(
  _In_  HMODULE           hSrcModule,
  _In_  LPCTSTR           pSrcResource,
  _In_  ID3DX11ThreadPump *pPump,
  _In_  D3DX11_IMAGE_INFO *pSrcInfo,
  _Out_ HRESULT           *pHResult
);
```



## Parameters

<dl> <dt>

*hSrcModule* \[in\]
</dt> <dd>

Type: **[**HMODULE**](/windows/desktop/WinProg/windows-data-types)**

Module where the resource is loaded. Set this parameter to **NULL** to specify the module associated with the image that the operating system used to create the current process.

</dd> <dt>

*pSrcResource* \[in\]
</dt> <dd>

Type: **[**LPCTSTR**](/windows/desktop/WinProg/windows-data-types)**

Pointer to a string that specifies the filename. If the compiler settings require Unicode, the data type LPCTSTR resolves to LPCWSTR. Otherwise, the data type resolves to LPCSTR. See Remarks.

</dd> <dt>

*pPump* \[in\]
</dt> <dd>

Type: **[**ID3DX11ThreadPump**](./id3dx11threadpump-1d47459670.md)\***

Optional thread pump that can be used to load the info asynchronously. Can be **NULL**. See [**ID3DX11ThreadPump Interface**](./id3dx11threadpump-1d47459670.md).

</dd> <dt>

*pSrcInfo* \[in\]
</dt> <dd>

Type: **[**D3DX11\_IMAGE\_INFO**](./d3dx11-image-info-0cc168c294.md)\***

Pointer to a D3DX11\_IMAGE\_INFO structure to be filled with the description of the data in the source file.

</dd> <dt>

*pHResult* \[out\]
</dt> <dd>

Type: **[**HRESULT**](https://msdn.microsoft.com/library/Bb401631(v=MSDN.10).aspx)\***

A pointer to the return value. May be **NULL**. If *pPump* is not **NULL**, then *pHResult* must be a valid memory location until the asynchronous execution completes.

</dd> </dl>

## Return value

Type: **[**HRESULT**](https://msdn.microsoft.com/library/Bb401631(v=MSDN.10).aspx)**

If the function succeeds, the return value is D3D\_OK. If the function fails, the return value can be the following: D3DERR\_INVALIDCALL

## Remarks

The compiler setting also determines the function version. If Unicode is defined, the function call resolves to **D3DX11GetImageInfoFromResourceW**. Otherwise, the function call resolves to **D3DX11GetImageInfoFromResourceA** because ANSI strings are being used.

## Requirements



| Requirement | Value |
|--------------------|----------------------------------------------------------------------------------------|
| Header<br/>  | <dl> <dt>D3DX11tex.h</dt> </dl> |
| Library<br/> | <dl> <dt>D3DX11.lib</dt> </dl>  |



## See also

<dl> <dt>

[D3DX Functions](./d3d11-graphics-reference-d3dx11-functions-e9c2bae664.md)
</dt> </dl>