Source: [https://learn.microsoft.com/en-us/windows/win32/api/D3D11/ne-d3d11-d3d11_resource_dimension](<https://learn.microsoft.com/en-us/windows/win32/api/D3D11/ne-d3d11-d3d11_resource_dimension>)

# D3D11_RESOURCE_DIMENSION enumeration


## -description

Identifies the type of resource being used.

## -enum-fields

### -field D3D11_RESOURCE_DIMENSION_UNKNOWN:0

Resource is of unknown type.

### -field D3D11_RESOURCE_DIMENSION_BUFFER:1

Resource is a buffer.

### -field D3D11_RESOURCE_DIMENSION_TEXTURE1D:2

Resource is a 1D texture.

### -field D3D11_RESOURCE_DIMENSION_TEXTURE2D:3

Resource is a 2D texture.

### -field D3D11_RESOURCE_DIMENSION_TEXTURE3D:4

Resource is a 3D texture.

## -remarks

This enumeration is used in <a href="/windows/desktop/api/d3d11/nf-d3d11-id3d11resource-gettype">ID3D11Resource::GetType</a>.

## -see-also

<a href="/windows/desktop/direct3d11/d3d11-graphics-reference-resource-enums">Resource Enumerations</a>