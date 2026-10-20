Source: [https://learn.microsoft.com/en-us/windows/win32/api/D3D11/ns-d3d11-d3d11_buffer_srv](<https://learn.microsoft.com/en-us/windows/win32/api/D3D11/ns-d3d11-d3d11_buffer_srv>)

# D3D11_BUFFER_SRV structure


## -description

Specifies the elements in a buffer resource to use in a shader-resource view.

## -struct-fields

### -field FirstElement

Type: <b><a href="/windows/desktop/WinProg/windows-data-types">UINT</a></b>

Index of the first element to access.

### -field ElementOffset

Type: <b><a href="/windows/desktop/WinProg/windows-data-types">UINT</a></b>

The offset of the first element in the view to access, relative to element 0.

### -field NumElements

Type: <b><a href="/windows/desktop/WinProg/windows-data-types">UINT</a></b>

The total number of elements in the view.

### -field ElementWidth

Type: <b><a href="/windows/desktop/WinProg/windows-data-types">UINT</a></b>

The width of each element (in bytes).
              This can be determined from the format stored in the shader-resource-view description.

## -remarks

The <b>D3D11_BUFFER_SRV</b> structure is a member of the  <a href="/windows/desktop/api/d3d11/ns-d3d11-d3d11_shader_resource_view_desc">D3D11_SHADER_RESOURCE_VIEW_DESC</a> structure, which represents a shader-resource view description. You can create a shader-resource view by calling the <a href="/windows/desktop/api/d3d11/nf-d3d11-id3d11device-createshaderresourceview">ID3D11Device::CreateShaderResourceView</a> method.

## -see-also

<a href="/windows/desktop/direct3d11/d3d11-graphics-reference-resource-structures">Resource Structures</a>