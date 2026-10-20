Source: [https://learn.microsoft.com/en-us/windows/win32/direct3d11/d3dx11-image-info](<https://learn.microsoft.com/en-us/windows/win32/direct3d11/d3dx11-image-info>)

# D3DX11\_IMAGE\_INFO structure

> [!Note]  
> The D3DX (D3DX 9, D3DX 10, and D3DX 11) utility library is deprecated for Windows 8 and is not supported for Windows Store apps.

 

Optionally provide information to texture loader APIs to control how textures get loaded. A value of D3DX11\_DEFAULT for any of these parameters will cause D3DX to automatically use the value from the source file.

## Syntax


```C++
typedef struct D3DX11_IMAGE_INFO {
  UINT                     Width;
  UINT                     Height;
  UINT                     Depth;
  UINT                     ArraySize;
  UINT                     MipLevels;
  UINT                     MiscFlags;
  DXGI_FORMAT              Format;
  D3D11_RESOURCE_DIMENSION ResourceDimension;
  D3DX11_IMAGE_FILE_FORMAT ImageFileFormat;
} D3DX11_IMAGE_INFO, *LPD3DX11_IMAGE_INFO;
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

**ArraySize**
</dt> <dd>

Type: **[**UINT**](/windows/desktop/WinProg/windows-data-types)**

</dd> <dd>

The number of elements in the array.

</dd> <dt>

**MipLevels**
</dt> <dd>

Type: **[**UINT**](/windows/desktop/WinProg/windows-data-types)**

</dd> <dd>

The maximum number of mipmap levels in the texture. See the remarks in [**D3D11\_TEX1D\_SRV**](./ns-d3d11-d3d11_tex1d_srv-088e577773.md). Using 0 or D3DX11\_DEFAULT will cause a full mipmap chain to be created.

</dd> <dt>

**MiscFlags**
</dt> <dd>

Type: **[**UINT**](/windows/desktop/WinProg/windows-data-types)**

</dd> <dd>

Miscellaneous resource properties specified with a [**D3D11\_RESOURCE\_MISC\_FLAG**](./ne-d3d11-d3d11_resource_misc_flag-f85f09a16f.md) flag.

</dd> <dt>

**Format**
</dt> <dd>

Type: **[**DXGI\_FORMAT**](/windows/desktop/api/dxgiformat/ne-dxgiformat-dxgi_format)**

</dd> <dd>

A [**DXGI\_FORMAT**](/windows/desktop/api/dxgiformat/ne-dxgiformat-dxgi_format) enumeration specifying the format the texture will be in after it is loaded.

</dd> <dt>

**ResourceDimension**
</dt> <dd>

Type: **[**D3D11\_RESOURCE\_DIMENSION**](./ne-d3d11-d3d11_resource_dimension-d235061312.md)**

</dd> <dd>

A [**D3D11\_RESOURCE\_DIMENSION**](./ne-d3d11-d3d11_resource_dimension-d235061312.md) value, which identifies the type of resource.

</dd> <dt>

**ImageFileFormat**
</dt> <dd>

Type: **[**D3DX11\_IMAGE\_FILE\_FORMAT**](./d3dx11-image-file-format-77284c5dc9.md)**

</dd> <dd>

A [**D3DX11\_IMAGE\_FILE\_FORMAT**](./d3dx11-image-file-format-77284c5dc9.md) value, which identifies the image format.

</dd> </dl>

## Remarks

This structure is used by methods such as: [**D3DX11GetImageInfoFromFile**](./d3dx11getimageinfofromfile-60fc03e113.md), [**D3DX11GetImageInfoFromMemory**](./d3dx11getimageinfofrommemory-cf5c1d62da.md), or [**D3DX11GetImageInfoFromResource**](./d3dx11getimageinfofromresource-5887f9c1ca.md).

## Requirements



| Requirement | Value |
|-------------------|----------------------------------------------------------------------------------------|
| Header<br/> | <dl> <dt>D3DX11tex.h</dt> </dl> |



## See also

<dl> <dt>

[D3DX Structures](./d3d11-graphics-reference-d3dx11-structures-07eae17c39.md)
</dt> </dl>