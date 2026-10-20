Source: [https://learn.microsoft.com/en-us/windows/win32/api/D3D11/ne-d3d11-d3d11_color_write_enable](<https://learn.microsoft.com/en-us/windows/win32/api/D3D11/ne-d3d11-d3d11_color_write_enable>)

# D3D11_COLOR_WRITE_ENABLE enumeration


## -description

Identify which components of each pixel of a render target are writable during blending.

## -enum-fields

### -field D3D11_COLOR_WRITE_ENABLE_RED:1

Allow data to be stored in the red component.

### -field D3D11_COLOR_WRITE_ENABLE_GREEN:2

Allow data to be stored in the green component.

### -field D3D11_COLOR_WRITE_ENABLE_BLUE:4

Allow data to be stored in the blue component.

### -field D3D11_COLOR_WRITE_ENABLE_ALPHA:8

Allow data to be stored in the alpha component.

### -field D3D11_COLOR_WRITE_ENABLE_ALL

Allow data to be stored in all components.

## -remarks

These flags can be combined with a bitwise OR.

## -see-also

<a href="/windows/desktop/direct3d11/d3d11-graphics-reference-d3d11-core-enums">Core Enumerations</a>