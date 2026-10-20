Source: [https://learn.microsoft.com/en-us/windows/win32/api/D3D11/ne-d3d11-d3d11_texture_address_mode](<https://learn.microsoft.com/en-us/windows/win32/api/D3D11/ne-d3d11-d3d11_texture_address_mode>)

# D3D11_TEXTURE_ADDRESS_MODE enumeration


## -description

Identify a technique for resolving texture coordinates that are outside of the boundaries of a texture.

## -enum-fields

### -field D3D11_TEXTURE_ADDRESS_WRAP:1

Tile the texture at every (u,v) integer junction. For example, for u values between 0 and 3, the texture is repeated three times.

### -field D3D11_TEXTURE_ADDRESS_MIRROR:2

Flip the texture at every (u,v) integer junction. For u values between 0 and 1, for example, the texture is addressed normally; between 1 and 2, the texture is flipped (mirrored); between 2 and 3, the texture is normal again; and so on.

### -field D3D11_TEXTURE_ADDRESS_CLAMP:3

Texture coordinates outside the range [0.0, 1.0] are set to the texture color at 0.0 or 1.0, respectively.

### -field D3D11_TEXTURE_ADDRESS_BORDER:4

Texture coordinates outside the range [0.0, 1.0] are set to the border color specified in <a href="/windows/desktop/api/d3d11/ns-d3d11-d3d11_sampler_desc">D3D11_SAMPLER_DESC</a> or HLSL code.

### -field D3D11_TEXTURE_ADDRESS_MIRROR_ONCE:5

Similar to D3D11_TEXTURE_ADDRESS_MIRROR and D3D11_TEXTURE_ADDRESS_CLAMP. Takes the absolute value of the texture coordinate (thus, mirroring around 0), and then clamps to the maximum value.

## -see-also

<a href="/windows/desktop/direct3d11/d3d11-graphics-reference-d3d11-core-enums">Core Enumerations</a>