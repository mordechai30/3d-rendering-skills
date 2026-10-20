Source: [https://learn.microsoft.com/en-us/windows/win32/api/D3D11/ns-d3d11-d3d11_texcube_array_srv](<https://learn.microsoft.com/en-us/windows/win32/api/D3D11/ns-d3d11-d3d11_texcube_array_srv>)

# D3D11_TEXCUBE_ARRAY_SRV structure


## -description

Specifies the subresources from an array of cube textures to use in a shader-resource view.

## -struct-fields

### -field MostDetailedMip

Type: <b><a href="/windows/desktop/WinProg/windows-data-types">UINT</a></b>

Index of the most detailed mipmap level to use; this number is between 0 and <b>MipLevels</b> (from the original TextureCube for which <a href="/windows/desktop/api/d3d11/nf-d3d11-id3d11device-createshaderresourceview">ID3D11Device::CreateShaderResourceView</a> creates a view) -1.

### -field MipLevels

Type: <b><a href="/windows/desktop/WinProg/windows-data-types">UINT</a></b>

The maximum number of mipmap levels for the view of the texture. See the remarks in <a href="/windows/desktop/api/d3d11/ns-d3d11-d3d11_tex1d_srv">D3D11_TEX1D_SRV</a>.

Set to -1 to indicate all the mipmap levels from <b>MostDetailedMip</b> on down to least detailed.

### -field First2DArrayFace

Type: <b><a href="/windows/desktop/WinProg/windows-data-types">UINT</a></b>

Index of the first 2D texture to use.

### -field NumCubes

Type: <b><a href="/windows/desktop/WinProg/windows-data-types">UINT</a></b>

Number of cube textures in the array.

## -remarks

This structure is one member of a shader-resource-view description (see <a href="/windows/desktop/api/d3d11/ns-d3d11-d3d11_shader_resource_view_desc">D3D11_SHADER_RESOURCE_VIEW_DESC</a>).

## -see-also

<a href="/windows/desktop/direct3d11/d3d11-graphics-reference-resource-structures">Resource Structures</a>