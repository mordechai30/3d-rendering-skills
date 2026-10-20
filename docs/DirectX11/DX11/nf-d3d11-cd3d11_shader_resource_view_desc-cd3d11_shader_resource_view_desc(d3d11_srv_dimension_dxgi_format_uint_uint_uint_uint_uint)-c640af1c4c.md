Source: [https://learn.microsoft.com/en-us/windows/win32/api/d3d11/nf-d3d11-cd3d11_shader_resource_view_desc-cd3d11_shader_resource_view_desc(d3d11_srv_dimension_dxgi_format_uint_uint_uint_uint_uint)](<https://learn.microsoft.com/en-us/windows/win32/api/d3d11/nf-d3d11-cd3d11_shader_resource_view_desc-cd3d11_shader_resource_view_desc(d3d11_srv_dimension_dxgi_format_uint_uint_uint_uint_uint)>)

# CD3D11_SHADER_RESOURCE_VIEW_DESC::CD3D11_SHADER_RESOURCE_VIEW_DESC(D3D11_SRV_DIMENSION,DXGI_FORMAT,UINT,UINT,UINT,UINT,UINT)


## -description

Instantiates a new instance of a <a href="/previous-versions/windows/desktop/legacy/jj151684(v=vs.85)">CD3D11_SHADER_RESOURCE_VIEW_DESC</a> structure that is initialized with <a href="/windows/desktop/api/d3d11/ns-d3d11-d3d11_shader_resource_view_desc">D3D11_SHADER_RESOURCE_VIEW_DESC</a> values.

## -parameters

### -param viewDimension

Type: <b><a href="/previous-versions/windows/desktop/legacy/ff476217(v=vs.85)">D3D11_SRV_DIMENSION</a></b>

A <a href="/previous-versions/windows/desktop/legacy/ff476217(v=vs.85)">D3D11_SRV_DIMENSION</a>-typed value that specifies the resource type of the view.

### -param format

Type: <b><a href="/windows/desktop/api/dxgiformat/ne-dxgiformat-dxgi_format">DXGI_FORMAT</a></b>

A <a href="/windows/desktop/api/dxgiformat/ne-dxgiformat-dxgi_format">DXGI_FORMAT</a>-typed value that specifies the viewing format.

### -param mostDetailedMip

Type: <b><a href="/windows/desktop/WinProg/windows-data-types">UINT</a></b>

Index of the most detailed mipmap level to use; this number is from 0 to <i>mipLevels</i> -1. For a buffer, this is the number of bytes between the beginning of the buffer and the first element to access.

<b>FirstElement</b> of <a href="/windows/desktop/api/d3d11/ns-d3d11-d3d11_buffer_srv">D3D11_BUFFER_SRV</a>.

### -param mipLevels

Type: <b><a href="/windows/desktop/WinProg/windows-data-types">UINT</a></b>

The maximum number of mipmap levels for the view.  For a buffer, this is the total number of elements in the view. <b>NumElements</b> of <a href="/windows/desktop/api/d3d11/ns-d3d11-d3d11_buffer_srv">D3D11_BUFFER_SRV</a>.

### -param firstArraySlice

Type: <b><a href="/windows/desktop/WinProg/windows-data-types">UINT</a></b>

The index of the first element to use in an array of elements.

<b>First2DArrayFace</b> of <a href="/windows/desktop/api/d3d11/ns-d3d11-d3d11_texcube_array_srv">D3D11_TEXCUBE_ARRAY_SRV</a>.

### -param arraySize

Type: <b><a href="/windows/desktop/WinProg/windows-data-types">UINT</a></b>

Number of elements in the array. <b>NumCubes</b> of <a href="/windows/desktop/api/d3d11/ns-d3d11-d3d11_texcube_array_srv">D3D11_TEXCUBE_ARRAY_SRV</a>.

### -param flags

Type: <b><a href="/windows/desktop/WinProg/windows-data-types">UINT</a></b>

A <a href="/windows/desktop/api/d3d11/ne-d3d11-d3d11_bufferex_srv_flag">D3D11_BUFFEREX_SRV_FLAG</a>-typed value that identifies view options for a buffer. For <a href="/windows/desktop/api/d3d11/ns-d3d11-d3d11_bufferex_srv">D3D11_BUFFEREX_SRV</a> only.

## -see-also

<a href="/previous-versions/windows/desktop/legacy/jj151684(v=vs.85)">CD3D11_SHADER_RESOURCE_VIEW_DESC</a>