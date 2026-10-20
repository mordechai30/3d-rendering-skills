Source: [https://learn.microsoft.com/en-us/windows/win32/direct3d11/d3dx11-channel-flag](<https://learn.microsoft.com/en-us/windows/win32/direct3d11/d3dx11-channel-flag>)

# D3DX11\_CHANNEL\_FLAG enumeration

> [!Note]  
> The D3DX (D3DX 9, D3DX 10, and D3DX 11) utility library is deprecated for Windows 8 and is not supported for Windows Store apps.

 

These flags are used by functions which operate on one or more channels in a texture.

## Syntax


```C++
typedef enum D3DX11_CHANNEL_FLAG { 
  D3DX11_CHANNEL_RED        = (1 << 0),
  D3DX11_CHANNEL_BLUE       = (1 << 1),
  D3DX11_CHANNEL_GREEN      = (1 << 2),
  D3DX11_CHANNEL_ALPHA      = (1 << 3),
  D3DX11_CHANNEL_LUMINANCE  = (1 << 4)
} D3DX11_CHANNEL_FLAG, *LPD3DX11_CHANNEL_FLAG;
```



## Constants

<dl> <dt>

<span id="D3DX11_CHANNEL_RED"></span><span id="d3dx11_channel_red"></span>**D3DX11\_CHANNEL\_RED**
</dt> <dd>

Indicates the red channel should be used.

</dd> <dt>

<span id="D3DX11_CHANNEL_BLUE"></span><span id="d3dx11_channel_blue"></span>**D3DX11\_CHANNEL\_BLUE**
</dt> <dd>

Indicates the blue channel should be used.

</dd> <dt>

<span id="D3DX11_CHANNEL_GREEN"></span><span id="d3dx11_channel_green"></span>**D3DX11\_CHANNEL\_GREEN**
</dt> <dd>

Indicates the green channel should be used.

</dd> <dt>

<span id="D3DX11_CHANNEL_ALPHA"></span><span id="d3dx11_channel_alpha"></span>**D3DX11\_CHANNEL\_ALPHA**
</dt> <dd>

Indicates the alpha channel should be used.

</dd> <dt>

<span id="D3DX11_CHANNEL_LUMINANCE"></span><span id="d3dx11_channel_luminance"></span>**D3DX11\_CHANNEL\_LUMINANCE**
</dt> <dd>

Indicates the luminaces of the red, green, and blue channels should be used.

</dd> </dl>

## Requirements



| Requirement | Value |
|-------------------|----------------------------------------------------------------------------------------|
| Header<br/> | <dl> <dt>D3DX11tex.h</dt> </dl> |



## See also

<dl> <dt>

[D3DX Enumerations](./d3d11-graphics-reference-d3dx11-enums-7704a2161a.md)
</dt> </dl>