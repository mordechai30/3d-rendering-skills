Source: [https://learn.microsoft.com/en-us/windows/win32/api/D3D11/ns-d3d11-d3d11_tex2dms_array_srv](<https://learn.microsoft.com/en-us/windows/win32/api/D3D11/ns-d3d11-d3d11_tex2dms_array_srv>)

# D3D11_TEX2DMS_ARRAY_SRV structure


## -description

Specifies the subresources from an array of multisampled 2D textures to use in a shader-resource view.

## -struct-fields

### -field FirstArraySlice

Type: <b><a href="/windows/desktop/WinProg/windows-data-types">UINT</a></b>

The index of the first texture to use in an array of textures.

### -field ArraySize

Type: <b><a href="/windows/desktop/WinProg/windows-data-types">UINT</a></b>

Number of textures to use.

## -remarks

This structure is one member of a shader-resource-view description (see <a href="/windows/desktop/api/d3d11/ns-d3d11-d3d11_shader_resource_view_desc">D3D11_SHADER_RESOURCE_VIEW_DESC</a>).

## -see-also

<a href="/windows/desktop/direct3d11/d3d11-graphics-reference-resource-structures">Resource Structures</a>