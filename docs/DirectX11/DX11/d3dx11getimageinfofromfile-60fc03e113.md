Source: [https://learn.microsoft.com/en-us/windows/win32/direct3d11/d3dx11getimageinfofromfile](<https://learn.microsoft.com/en-us/windows/win32/direct3d11/d3dx11getimageinfofromfile>)

# D3DX11GetImageInfoFromFile function

> [!Note]  
> The D3DX (D3DX 9, D3DX 10, and D3DX 11) utility library is deprecated for Windows 8 and is not supported for Windows Store apps.

 

> [!Note]  
> Instead of using this function, we recommend that you use the [DirectXTex](https://github.com/Microsoft/DirectXTex) library, **GetMetadataFromXXXFile** (where XXX is WIC, DDS, or TGA; WIC doesn't support DDS and TGA; D3DX 9 supported TGA as a common art source format for games).

 

Retrieves information about a given image file.

## Syntax


```C++
HRESULT D3DX11GetImageInfoFromFile(
  _In_  LPCTSTR           pSrcFile,
  _In_  ID3DX11ThreadPump *pPump,
  _In_  D3DX11_IMAGE_INFO *pSrcInfo,
  _Out_ HRESULT           *pHResult
);
```



## Parameters

<dl> <dt>

*pSrcFile* \[in\]
</dt> <dd>

Type: **[**LPCTSTR**](/windows/desktop/WinProg/windows-data-types)**

File name of image to retrieve information about. If UNICODE or \_UNICODE are defined, this parameter type is LPCWSTR, otherwise, the type is LPCSTR.

</dd> <dt>

*pPump* \[in\]
</dt> <dd>

Type: **[**ID3DX11ThreadPump**](./id3dx11threadpump-1d47459670.md)\***

Optional thread pump that can be used to load the info asynchronously. Can be **NULL**. See [**ID3DX11ThreadPump Interface**](./id3dx11threadpump-1d47459670.md).

</dd> <dt>

*pSrcInfo* \[in\]
</dt> <dd>

Type: **[**D3DX11\_IMAGE\_INFO**](./d3dx11-image-info-0cc168c294.md)\***

Pointer to a [**D3DX11\_IMAGE\_INFO**](./d3dx11-image-info-0cc168c294.md) to be filled with the description of the data in the source file.

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

This function supports both Unicode and ANSI strings.

## Requirements



| Requirement | Value |
|--------------------|----------------------------------------------------------------------------------------|
| Header<br/>  | <dl> <dt>D3DX11tex.h</dt> </dl> |
| Library<br/> | <dl> <dt>D3DX11.lib</dt> </dl>  |



## See also

<dl> <dt>

[D3DX Functions](./d3d11-graphics-reference-d3dx11-functions-e9c2bae664.md)
</dt> </dl>