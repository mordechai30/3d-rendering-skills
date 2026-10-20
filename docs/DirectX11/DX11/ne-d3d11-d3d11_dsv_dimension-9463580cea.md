Source: [https://learn.microsoft.com/en-us/windows/win32/api/D3D11/ne-d3d11-d3d11_dsv_dimension](<https://learn.microsoft.com/en-us/windows/win32/api/D3D11/ne-d3d11-d3d11_dsv_dimension>)

# D3D11_DSV_DIMENSION enumeration


## -description

Specifies how to access a resource used in a depth-stencil view.

## -enum-fields

### -field D3D11_DSV_DIMENSION_UNKNOWN:0

<i>D3D11_DSV_DIMENSION_UNKNOWN</i> is not a valid value for <a href="/windows/desktop/api/d3d11/ns-d3d11-d3d11_depth_stencil_view_desc">D3D11_DEPTH_STENCIL_VIEW_DESC</a> and is not used.

### -field D3D11_DSV_DIMENSION_TEXTURE1D:1

The resource will be accessed as a 1D texture.

### -field D3D11_DSV_DIMENSION_TEXTURE1DARRAY:2

The resource will be accessed as an array of 1D textures.

### -field D3D11_DSV_DIMENSION_TEXTURE2D:3

The resource will be accessed as a 2D texture.

### -field D3D11_DSV_DIMENSION_TEXTURE2DARRAY:4

The resource will be accessed as an array of 2D textures.

### -field D3D11_DSV_DIMENSION_TEXTURE2DMS:5

The resource will be accessed as a 2D texture with multisampling.

### -field D3D11_DSV_DIMENSION_TEXTURE2DMSARRAY:6

The resource will be accessed as an array of 2D textures with multisampling.

## -remarks

This enumeration is used in <a href="/windows/desktop/api/d3d11/ns-d3d11-d3d11_depth_stencil_view_desc">D3D11_DEPTH_STENCIL_VIEW_DESC</a> to create a depth-stencil view.

## -see-also

<a href="/windows/desktop/direct3d11/d3d11-graphics-reference-resource-enums">Resource Enumerations</a>