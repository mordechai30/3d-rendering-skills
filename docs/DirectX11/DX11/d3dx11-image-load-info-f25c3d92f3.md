Source: [https://learn.microsoft.com/en-us/windows/win32/direct3d11/d3dx11-image-load-info](<https://learn.microsoft.com/en-us/windows/win32/direct3d11/d3dx11-image-load-info>)

# D3DX11\_IMAGE\_LOAD\_INFO structure

> [!Note]  
> The D3DX (D3DX 9, D3DX 10, and D3DX 11) utility library is deprecated for Windows 8 and is not supported for Windows Store apps.

 

Optionally provide information to texture loader APIs to control how textures get loaded. A value of D3DX11\_DEFAULT for any of these parameters will cause D3DX to automatically use the value from the source file.

## Syntax


```C++
typedef struct D3DX11_IMAGE_LOAD_INFO {
  UINT              Width;
  UINT              Height;
  UINT              Depth;
  UINT              FirstMipLevel;
  UINT              MipLevels;
  D3D11_USAGE       Usage;
  UINT              BindFlags;
  UINT              CpuAccessFlags;
  UINT              MiscFlags;
  DXGI_FORMAT       Format;
  UINT              Filter;
  UINT              MipFilter;
  D3DX11_IMAGE_INFO *pSrcInfo;
} D3DX11_IMAGE_LOAD_INFO, *LPD3DX11_IMAGE_LOAD_INFO;
```



## Members

<dl> <dt>

**Width**
</dt> <dd>

Type: **[**UINT**](/windows/desktop/WinProg/windows-data-types)**

</dd> <dd>

The target width of the texture. If the actual width of the texture is larger or smaller than this value then the texture will be scaled up or down to fit this target width.

</dd> <dt>

**Height**
</dt> <dd>

Type: **[**UINT**](/windows/desktop/WinProg/windows-data-types)**

</dd> <dd>

The target height of the texture. If the actual height of the texture is larger or smaller than this value then the texture will be scaled up or down to fit this target height.

</dd> <dt>

**Depth**
</dt> <dd>

Type: **[**UINT**](/windows/desktop/WinProg/windows-data-types)**

</dd> <dd>

The depth of the texture. This only applies to volume textures.

</dd> <dt>

**FirstMipLevel**
</dt> <dd>

Type: **[**UINT**](/windows/desktop/WinProg/windows-data-types)**

</dd> <dd>

The highest resolution mipmap level of the texture. If this is greater than 0, then after the texture is loaded FirstMipLevel will be mapped to mipmap level 0.

</dd> <dt>

**MipLevels**
</dt> <dd>

Type: **[**UINT**](/windows/desktop/WinProg/windows-data-types)**

</dd> <dd>

The maximum number of mipmap levels in the texture. See the remarks in [**D3D11\_TEX1D\_SRV**](./ns-d3d11-d3d11_tex1d_srv-088e577773.md). Using 0 or D3DX11\_DEFAULT will cause a full mipmap chain to be created.

</dd> <dt>

**Usage**
</dt> <dd>

Type: **[**D3D11\_USAGE**](./ne-d3d11-d3d11_usage-8197affe09.md)**

</dd> <dd>

The way the texture resource is intended to be used. See [**D3D11\_USAGE**](./ne-d3d11-d3d11_usage-8197affe09.md).

</dd> <dt>

**BindFlags**
</dt> <dd>

Type: **[**UINT**](/windows/desktop/WinProg/windows-data-types)**

</dd> <dd>

The pipeline stages that the texture will be allowed to bind to. See [**D3D11\_BIND\_FLAG**](./ne-d3d11-d3d11_bind_flag-78d4ee3d0d.md).

</dd> <dt>

**CpuAccessFlags**
</dt> <dd>

Type: **[**UINT**](/windows/desktop/WinProg/windows-data-types)**

</dd> <dd>

The access permissions the cpu will have for the texture resource. See [**D3D11\_CPU\_ACCESS\_FLAG**](./ne-d3d11-d3d11_cpu_access_flag-2c51d58b52.md).

</dd> <dt>

**MiscFlags**
</dt> <dd>

Type: **[**UINT**](/windows/desktop/WinProg/windows-data-types)**

</dd> <dd>

Miscellaneous resource properties (see [**D3D11\_RESOURCE\_MISC\_FLAG**](./ne-d3d11-d3d11_resource_misc_flag-f85f09a16f.md)).

</dd> <dt>

**Format**
</dt> <dd>

Type: **[**DXGI\_FORMAT**](/windows/desktop/api/dxgiformat/ne-dxgiformat-dxgi_format)**

</dd> <dd>

A [**DXGI\_FORMAT**](/windows/desktop/api/dxgiformat/ne-dxgiformat-dxgi_format) enumeration indicating the format the texture will be in after it is loaded.

</dd> <dt>

**Filter**
</dt> <dd>

Type: **[**UINT**](/windows/desktop/WinProg/windows-data-types)**

</dd> <dd>

Filter the texture using the specified filter (only when resampling). See [**D3DX11\_FILTER\_FLAG**](./d3dx11-filter-flag-5bb78a91af.md).

</dd> <dt>

**MipFilter**
</dt> <dd>

Type: **[**UINT**](/windows/desktop/WinProg/windows-data-types)**

</dd> <dd>

Filter the texture mip levels using the specified filter (only if generating mipmaps). Valid values are D3DX11\_FILTER\_NONE, D3DX11\_FILTER\_POINT, D3DX11\_FILTER\_LINEAR, or D3DX11\_FILTER\_TRIANGLE. See [**D3DX11\_FILTER\_FLAG**](./d3dx11-filter-flag-5bb78a91af.md).

</dd> <dt>

**pSrcInfo**
</dt> <dd>

Type: **[**D3DX11\_IMAGE\_INFO**](./d3dx11-image-info-0cc168c294.md)\***

</dd> <dd>

Information about the original image. See [**D3DX11\_IMAGE\_INFO**](./d3dx11-image-info-0cc168c294.md). Can be obtained with [**D3DX11GetImageInfoFromFile**](./d3dx11getimageinfofromfile-60fc03e113.md), [**D3DX11GetImageInfoFromMemory**](./d3dx11getimageinfofrommemory-cf5c1d62da.md), or [**D3DX11GetImageInfoFromResource**](./d3dx11getimageinfofromresource-5887f9c1ca.md).

</dd> </dl>

## Remarks

When initializing the structure, you may set any member to D3DX11\_DEFAULT and D3DX will initialize it with a default value from the source texture when the texture is loaded.

This structure can be used by APIs that:

-   Create resources, such as [**D3DX11CreateTextureFromFile**](./d3dx11createtexturefromfile-0ef1c79cb6.md) and [**D3DX11CreateShaderResourceViewFromFile**](./d3dx11createshaderresourceviewfromfile-b36d70591a.md).
-   Create data processors, such as [**D3DX11CreateAsyncTextureInfoProcessor**](./d3dx11createasynctextureinfoprocessor-90a4fd74d7.md) or [**D3DX11CreateAsyncShaderResourceViewProcessor**](./d3dx11createasyncshaderresourceviewprocessor-794b98f1ba.md).

The default values are:


```
    Width = D3DX11_DEFAULT;
    Height = D3DX11_DEFAULT;
    Depth = D3DX11_DEFAULT;
    FirstMipLevel = D3DX11_DEFAULT;
    MipLevels = D3DX11_DEFAULT;
    Usage = (D3D11_USAGE) D3DX11_DEFAULT;
    BindFlags = D3DX11_DEFAULT;
    CpuAccessFlags = D3DX11_DEFAULT;
    MiscFlags = D3DX11_DEFAULT;
    Format = DXGI_FORMAT_FROM_FILE;
    Filter = D3DX11_DEFAULT;
    MipFilter = D3DX11_DEFAULT;
    pSrcInfo = NULL;
```



Here is a brief example that uses this structure to supply the pixel format when loading a texture. For the complete code, see HDRFormats10.cpp in [HDRToneMappingCS11 Sample](https://msdn.microsoft.com/library/Ee416569(v=VS.85).aspx).


```
ID3D11ShaderResourceView* pCubeRV = NULL;
WCHAR strPath[MAX_PATH];
D3DX11_IMAGE_LOAD_INFO LoadInfo;

    DXUTFindDXSDKMediaFileCch( strPath, MAX_PATH, 
        L"Light Probes\\uffizi_cross.dds" );

    LoadInfo.Format = DXGI_FORMAT_R16G16B16A16_FLOAT;

    hr = D3DX11CreateShaderResourceViewFromFile( pd3dDevice, strPath, 
        &LoadInfo, NULL, &pCubeRV, NULL );
```



## Requirements



| Requirement | Value |
|-------------------|----------------------------------------------------------------------------------------|
| Header<br/> | <dl> <dt>D3DX11tex.h</dt> </dl> |



## See also

<dl> <dt>

[D3DX Structures](./d3d11-graphics-reference-d3dx11-structures-07eae17c39.md)
</dt> </dl>