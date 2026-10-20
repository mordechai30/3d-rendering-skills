Source: [https://learn.microsoft.com/en-us/windows/win32/api/D3D11_3/ns-d3d11_3-d3d11_tex2d_array_srv1](<https://learn.microsoft.com/en-us/windows/win32/api/D3D11_3/ns-d3d11_3-d3d11_tex2d_array_srv1>)

# D3D11_TEX2D_ARRAY_SRV1 structure


## -description

Describes the subresources from an array of 2D textures to use in a shader-resource view.

## -struct-fields

### -field MostDetailedMip

Index of the most detailed mipmap level to use; this number is between 0 and ( <b>MipLevels</b> (from the original Texture2D for which 
            <a href="/windows/desktop/api/d3d11_3/nf-d3d11_3-id3d11device3-createshaderresourceview1">ID3D11Device3::CreateShaderResourceView1</a> 
            creates a view) - 1).

### -field MipLevels

The maximum number of mipmap levels for the view of the texture. See the remarks in <a href="/windows/desktop/api/d3d11/ns-d3d11-d3d11_tex1d_srv">D3D11_TEX1D_SRV</a>.
            

Set to -1 to indicate all the mipmap levels from <b>MostDetailedMip</b> on down to least detailed.

### -field FirstArraySlice

The index of the first texture to use in an array of textures.

### -field ArraySize

Number of textures in the array.

### -field PlaneSlice

The index (plane slice number) of the plane to use in an array of textures.

## -see-also

<a href="/windows/desktop/direct3d11/d3d11-graphics-reference-resource-structures">Resource Structures</a>