Source: [https://learn.microsoft.com/en-us/windows/win32/api/d3d11/nf-d3d11-cd3d11_shader_resource_view_desc-cd3d11_shader_resource_view_desc(id3d11texture3d_dxgi_format_uint_uint)](<https://learn.microsoft.com/en-us/windows/win32/api/d3d11/nf-d3d11-cd3d11_shader_resource_view_desc-cd3d11_shader_resource_view_desc(id3d11texture3d_dxgi_format_uint_uint)>)

# CD3D11_SHADER_RESOURCE_VIEW_DESC::CD3D11_SHADER_RESOURCE_VIEW_DESC(ID3D11Texture3D,DXGI_FORMAT,UINT,UINT)


## -description

Instantiates a new instance of a <a href="/previous-versions/windows/desktop/legacy/jj151684(v=vs.85)">CD3D11_SHADER_RESOURCE_VIEW_DESC</a> structure that is initialized with 3D texture  values.

## -parameters

### -param pTex3D

A pointer to a **ID3D11Texture3D** interface for a 3D texture.

### -param format

A **DXGI_FORMAT**-typed value that specifies the viewing format.

### -param mostDetailedMip

Index of the most detailed mipmap level to use; this number is from 0 to *mipLevels* -1.

### -param mipLevels

The maximum number of mipmap levels for the view.

## -see-also

<a href="/previous-versions/windows/desktop/legacy/jj151684(v=vs.85)">CD3D11_SHADER_RESOURCE_VIEW_DESC</a>