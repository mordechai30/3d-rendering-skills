Source: [https://learn.microsoft.com/en-us/windows/win32/api/d3d11/nf-d3d11-cd3d11_shader_resource_view_desc-cd3d11_shader_resource_view_desc(id3d11texture1d_d3d11_srv_dimension_dxgi_format_uint_uint_uint_uint)](<https://learn.microsoft.com/en-us/windows/win32/api/d3d11/nf-d3d11-cd3d11_shader_resource_view_desc-cd3d11_shader_resource_view_desc(id3d11texture1d_d3d11_srv_dimension_dxgi_format_uint_uint_uint_uint)>)

# CD3D11_SHADER_RESOURCE_VIEW_DESC::CD3D11_SHADER_RESOURCE_VIEW_DESC(ID3D11Texture1D,D3D11_SRV_DIMENSION,DXGI_FORMAT,UINT,UINT,UINT,UINT)


## -description

Instantiates a new instance of a <a href="/previous-versions/windows/desktop/legacy/jj151684(v=vs.85)">CD3D11_SHADER_RESOURCE_VIEW_DESC</a> structure that is initialized with **D3D11_TEX1D_SRV** or **D3D11_TEX1D_ARRAY_SRV** values.

## -parameters

### -param pTex1D

A pointer to a **ID3D11Texture1D** interface for a 1D texture.

### -param viewDimension

A **D3D11_SRV_DIMENSION**-typed value that specifies the resource type of the view.

### -param format

A **DXGI_FORMAT**-typed value that specifies the viewing format.

### -param mostDetailedMip

Index of the most detailed mipmap level to use; this number is from 0 to *mipLevels* -1.

### -param mipLevels

The maximum number of mipmap levels for the view.

### -param firstArraySlice

The index of the first element to use in an array of elements.

### -param arraySize

Number of elements in the array.

## -see-also

<a href="/previous-versions/windows/desktop/legacy/jj151684(v=vs.85)">CD3D11_SHADER_RESOURCE_VIEW_DESC</a>