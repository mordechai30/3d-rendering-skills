Source: [https://learn.microsoft.com/en-us/windows/win32/direct3d11/d3dx11-normalmap-flag](<https://learn.microsoft.com/en-us/windows/win32/direct3d11/d3dx11-normalmap-flag>)

# D3DX11\_NORMALMAP\_FLAG enumeration

> [!Note]  
> The D3DX (D3DX 9, D3DX 10, and D3DX 11) utility library is deprecated for Windows 8 and is not supported for Windows Store apps.

 

Normal map options. You can combine any number of these flags by using a bitwise OR operation.

## Syntax


```C++
typedef enum D3DX11_NORMALMAP_FLAG { 
  D3DX11_NORMALMAP_MIRROR_U           = (1 << 16),
  D3DX11_NORMALMAP_MIRROR_V           = (2 << 16),
  D3DX11_NORMALMAP_MIRROR             = (3 << 16),
  D3DX11_NORMALMAP_INVERTSIGN         = (8 << 16),
  D3DX11_NORMALMAP_COMPUTE_OCCLUSION  = (16 << 16)
} D3DX11_NORMALMAP_FLAG, *LPD3DX11_NORMALMAP_FLAG;
```



## Constants

<dl> <dt>

<span id="D3DX11_NORMALMAP_MIRROR_U"></span><span id="d3dx11_normalmap_mirror_u"></span>**D3DX11\_NORMALMAP\_MIRROR\_U**
</dt> <dd>

Indicates that pixels off the edge of the texture on the U-axis should be mirrored, not wraped.

</dd> <dt>

<span id="D3DX11_NORMALMAP_MIRROR_V"></span><span id="d3dx11_normalmap_mirror_v"></span>**D3DX11\_NORMALMAP\_MIRROR\_V**
</dt> <dd>

Indicates that pixels off the edge of the texture on the V-axis should be mirrored, not wraped.

</dd> <dt>

<span id="D3DX11_NORMALMAP_MIRROR"></span><span id="d3dx11_normalmap_mirror"></span>**D3DX11\_NORMALMAP\_MIRROR**
</dt> <dd>

Same as D3DX11\_NORMALMAP\_MIRROR\_U \| D3DX11\_NORMALMAP\_MIRROR\_V.

</dd> <dt>

<span id="D3DX11_NORMALMAP_INVERTSIGN"></span><span id="d3dx11_normalmap_invertsign"></span>**D3DX11\_NORMALMAP\_INVERTSIGN**
</dt> <dd>

Inverts the direction of each normal.

</dd> <dt>

<span id="D3DX11_NORMALMAP_COMPUTE_OCCLUSION"></span><span id="d3dx11_normalmap_compute_occlusion"></span>**D3DX11\_NORMALMAP\_COMPUTE\_OCCLUSION**
</dt> <dd>

Computes the per pixel occlusion term and encodes it into the alpha. An Alpha of 1 means that the pixel is not obscured in any way, and an alpha of 0 would mean that the pixel is completely obscured.

</dd> </dl>

## Remarks

These flags are used by [**D3DX11ComputeNormalMap**](./d3dx11computenormalmap-1c9f14f78b.md).

## Requirements



| Requirement | Value |
|-------------------|----------------------------------------------------------------------------------------|
| Header<br/> | <dl> <dt>D3DX11tex.h</dt> </dl> |



## See also

<dl> <dt>

[D3DX Enumerations](./d3d11-graphics-reference-d3dx11-enums-7704a2161a.md)
</dt> </dl>