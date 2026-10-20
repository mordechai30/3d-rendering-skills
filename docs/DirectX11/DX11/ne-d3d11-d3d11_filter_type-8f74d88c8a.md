Source: [https://learn.microsoft.com/en-us/windows/win32/api/D3D11/ne-d3d11-d3d11_filter_type](<https://learn.microsoft.com/en-us/windows/win32/api/D3D11/ne-d3d11-d3d11_filter_type>)

# D3D11_FILTER_TYPE enumeration


## -description

Types of magnification or minification sampler filters.

## -enum-fields

### -field D3D11_FILTER_TYPE_POINT:0

Point filtering used as a texture magnification or minification filter. The texel with coordinates nearest to the desired pixel value is used. The texture filter to be used between mipmap levels is nearest-point mipmap filtering. The rasterizer uses the color from the texel of the nearest mipmap texture.

### -field D3D11_FILTER_TYPE_LINEAR:1

Bilinear interpolation filtering used as a texture magnification or minification filter. A weighted average of a 2 x 2 area of texels surrounding the desired pixel is used. The texture filter to use between mipmap levels is trilinear mipmap interpolation. The rasterizer linearly interpolates pixel color, using the texels of the two nearest mipmap textures.

## -see-also

<a href="/windows/desktop/direct3d11/d3d11-graphics-reference-d3d11-core-enums">Core Enumerations</a>