Source: [https://learn.microsoft.com/en-us/windows/win32/direct3d11/d3dx11-texture-load-info](<https://learn.microsoft.com/en-us/windows/win32/direct3d11/d3dx11-texture-load-info>)

# D3DX11\_TEXTURE\_LOAD\_INFO structure

> [!Note]  
> The D3DX (D3DX 9, D3DX 10, and D3DX 11) utility library is deprecated for Windows 8 and is not supported for Windows Store apps.

 

Describes parameters used to load a texture from another texture.

## Syntax


```C++
typedef struct _D3DX11_TEXTURE_LOAD_INFO {
  D3D11_BOX *pSrcBox;
  D3D11_BOX *pDstBox;
  UINT      SrcFirstMip;
  UINT      DstFirstMip;
  UINT      NumMips;
  UINT      SrcFirstElement;
  UINT      DstFirstElement;
  UINT      NumElements;
  UINT      Filter;
  UINT      MipFilter;
} D3DX11_TEXTURE_LOAD_INFO;
```



## Members

<dl> <dt>

**pSrcBox**
</dt> <dd>

Type: **[**D3D11\_BOX**](./ns-d3d11-d3d11_box-dfaf37e939.md)\***

</dd> <dd>

Source texture box (see [**D3D11\_BOX**](./ns-d3d11-d3d11_box-dfaf37e939.md)).

</dd> <dt>

**pDstBox**
</dt> <dd>

Type: **[**D3D11\_BOX**](./ns-d3d11-d3d11_box-dfaf37e939.md)\***

</dd> <dd>

Destination texture box (see [**D3D11\_BOX**](./ns-d3d11-d3d11_box-dfaf37e939.md)).

</dd> <dt>

**SrcFirstMip**
</dt> <dd>

Type: **[**UINT**](/windows/desktop/WinProg/windows-data-types)**

</dd> <dd>

Source texture mipmap level, see [**D3D11CalcSubresource**](./nf-d3d11-d3d11calcsubresource-2a0d71330a.md) for more detail.

</dd> <dt>

**DstFirstMip**
</dt> <dd>

Type: **[**UINT**](/windows/desktop/WinProg/windows-data-types)**

</dd> <dd>

Destination texture mipmap level, see [**D3D11CalcSubresource**](./nf-d3d11-d3d11calcsubresource-2a0d71330a.md) for more detail.

</dd> <dt>

**NumMips**
</dt> <dd>

Type: **[**UINT**](/windows/desktop/WinProg/windows-data-types)**

</dd> <dd>

Number of mipmap levels in the source texture.

</dd> <dt>

**SrcFirstElement**
</dt> <dd>

Type: **[**UINT**](/windows/desktop/WinProg/windows-data-types)**

</dd> <dd>

First element of the source texture.

</dd> <dt>

**DstFirstElement**
</dt> <dd>

Type: **[**UINT**](/windows/desktop/WinProg/windows-data-types)**

</dd> <dd>

First element of the destination texture.

</dd> <dt>

**NumElements**
</dt> <dd>

Type: **[**UINT**](/windows/desktop/WinProg/windows-data-types)**

</dd> <dd>

Number of elements to load.

</dd> <dt>

**Filter**
</dt> <dd>

Type: **[**UINT**](/windows/desktop/WinProg/windows-data-types)**

</dd> <dd>

Filtering options during resampling (see [**D3DX11\_FILTER\_FLAG**](./d3dx11-filter-flag-5bb78a91af.md)).

</dd> <dt>

**MipFilter**
</dt> <dd>

Type: **[**UINT**](/windows/desktop/WinProg/windows-data-types)**

</dd> <dd>

Filtering options when generating mip levels (see [**D3DX11\_FILTER\_FLAG**](./d3dx11-filter-flag-5bb78a91af.md)).

</dd> </dl>

## Remarks

This structure is used in a call to [**D3DX11LoadTextureFromTexture**](./d3dx11loadtexturefromtexture-5511d7382c.md).

The default values are:


```
    pSrcBox = NULL;
    pDstBox = NULL;
    SrcFirstMip = 0;
    DstFirstMip = 0;
    NumMips = D3DX11_DEFAULT;
    SrcFirstElement = 0;
    DstFirstElement = 0;
    NumElements = D3DX11_DEFAULT;
    Filter = D3DX11_DEFAULT;
    MipFilter = D3DX11_DEFAULT;
```



## Requirements



| Requirement | Value |
|-------------------|----------------------------------------------------------------------------------------|
| Header<br/> | <dl> <dt>D3DX11tex.h</dt> </dl> |



## See also

<dl> <dt>

[D3DX Structures](./d3d11-graphics-reference-d3dx11-structures-07eae17c39.md)
</dt> </dl>