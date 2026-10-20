Source: [https://learn.microsoft.com/en-us/windows/win32/api/D3D11_3/ns-d3d11_3-d3d11_tex2d_array_rtv1](<https://learn.microsoft.com/en-us/windows/win32/api/D3D11_3/ns-d3d11_3-d3d11_tex2d_array_rtv1>)

# D3D11_TEX2D_ARRAY_RTV1 structure


## -description

Describes the subresources from an array of 2D textures to use in a render-target view.

## -struct-fields

### -field MipSlice

The index of the mipmap level to use mip slice.

### -field FirstArraySlice

The index of the first texture to use in an array of textures.

### -field ArraySize

Number of textures in the array to use in the render-target view, starting from <b>FirstArraySlice</b>.

### -field PlaneSlice

The index (plane slice number) of the plane to use in an array of textures.

## -see-also

<a href="/windows/desktop/direct3d11/d3d11-graphics-reference-resource-structures">Resource Structures</a>