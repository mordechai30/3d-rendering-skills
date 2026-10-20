Source: [https://learn.microsoft.com/en-us/windows/win32/direct3d11/d3dx11createasynctextureinfoprocessor](<https://learn.microsoft.com/en-us/windows/win32/direct3d11/d3dx11createasynctextureinfoprocessor>)

# D3DX11CreateAsyncTextureInfoProcessor function

> [!Note]  
> The D3DX (D3DX 9, D3DX 10, and D3DX 11) utility library is deprecated for Windows 8 and is not supported for Windows Store apps. See Remarks.

 

Create a data processor to be used with a [**thread pump**](./id3dx11threadpump-1d47459670.md).

## Syntax


```C++
HRESULT D3DX11CreateAsyncTextureInfoProcessor(
  _In_  D3DX11_IMAGE_INFO    *pImageInfo,
  _Out_ ID3DX11DataProcessor **ppDataProcessor
);
```



## Parameters

<dl> <dt>

*pImageInfo* \[in\]
</dt> <dd>

Type: **[**D3DX11\_IMAGE\_INFO**](./d3dx11-image-info-0cc168c294.md)\***

Optional. Identifies the characteristics of a texture (see [**D3DX11\_IMAGE\_INFO**](./d3dx11-image-info-0cc168c294.md)) when the data processor is created; set this to **NULL** to read the characteristics of a texture when the texture is loaded.

</dd> <dt>

*ppDataProcessor* \[out\]
</dt> <dd>

Type: **[**ID3DX11DataProcessor**](./id3dx11dataprocessor-1d7ffa3059.md)\*\***

Address of a pointer to a buffer that contains the data processor created (see [**ID3DX11DataProcessor Interface**](./id3dx11dataprocessor-1d7ffa3059.md)).

</dd> </dl>

## Return value

Type: **[**HRESULT**](https://msdn.microsoft.com/library/Bb401631(v=MSDN.10).aspx)**

The return value is one of the values listed in [Direct3D 11 Return Codes](./d3d11-graphics-reference-returnvalues-2d2638a6a7.md).

## Remarks

This API does creates a data-processor interface; [**D3DX11CreateAsyncTextureProcessor**](./d3dx11createasynctextureprocessor-7025d76524.md) creates the data-processor interface and loads the texture.

There s no implementation of the  async loader  outside of D3DX 10, and D3DX 11.

For Windows Store apps, the DirectX samples (for example, the [Direct3D tutorial sample](https://github.com/microsoftarchive/msdn-code-gallery-microsoft/tree/master/Official%20Windows%20Platform%20Sample/Direct3D%20tutorial%20sample)) include the **BasicLoader** module that uses the Windows Runtime asynchronous programming model ([**AsyncBase**](/previous-versions/visualstudio/visual-studio-2012/br244878(v=vs.110))).

For Win32 desktop apps, you can use the [Concurrency Runtime](/previous-versions/visualstudio/visual-studio-2010/ee207192(v=vs.100)) to implement something similar to the Windows Runtime asynchronous programming model.

## Requirements



| Requirement | Value |
|--------------------|----------------------------------------------------------------------------------------|
| Header<br/>  | <dl> <dt>D3DX11tex.h</dt> </dl> |
| Library<br/> | <dl> <dt>D3DX11.lib</dt> </dl>  |



## See also

<dl> <dt>

[D3DX Functions](./d3d11-graphics-reference-d3dx11-functions-e9c2bae664.md)
</dt> </dl>