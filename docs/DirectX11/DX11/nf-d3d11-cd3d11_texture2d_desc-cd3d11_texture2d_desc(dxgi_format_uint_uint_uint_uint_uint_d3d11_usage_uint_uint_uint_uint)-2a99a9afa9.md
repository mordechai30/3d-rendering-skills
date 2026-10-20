Source: [https://learn.microsoft.com/en-us/windows/win32/api/d3d11/nf-d3d11-cd3d11_texture2d_desc-cd3d11_texture2d_desc(dxgi_format_uint_uint_uint_uint_uint_d3d11_usage_uint_uint_uint_uint)](<https://learn.microsoft.com/en-us/windows/win32/api/d3d11/nf-d3d11-cd3d11_texture2d_desc-cd3d11_texture2d_desc(dxgi_format_uint_uint_uint_uint_uint_d3d11_usage_uint_uint_uint_uint)>)

# CD3D11_TEXTURE2D_DESC::CD3D11_TEXTURE2D_DESC(DXGI_FORMAT,UINT,UINT,UINT,UINT,UINT,D3D11_USAGE,UINT,UINT,UINT,UINT)


## -description

Instantiates a new instance of a <a href="/previous-versions/windows/desktop/legacy/jj151700(v=vs.85)">CD3D11_TEXTURE2D_DESC</a> structure that is initialized with <a href="/windows/desktop/api/d3d11/ns-d3d11-d3d11_texture2d_desc">D3D11_TEXTURE2D_DESC</a> values.

## -parameters

### -param format

Type: <b><a href="/windows/desktop/api/dxgiformat/ne-dxgiformat-dxgi_format">DXGI_FORMAT</a></b>

A <a href="/windows/desktop/api/dxgiformat/ne-dxgiformat-dxgi_format">DXGI_FORMAT</a>-typed value that specifies the texture format.

### -param width

Type: <b><a href="/windows/desktop/WinProg/windows-data-types">UINT</a></b>

Texture width (in texels). The  range is from 1 to D3D11_REQ_TEXTURE2D_U_OR_V_DIMENSION (16384). For a texture cube-map, the  range is from 1 to D3D11_REQ_TEXTURECUBE_DIMENSION (16384). However, the range is actually constrained by the <a href="/windows/desktop/direct3d11/overviews-direct3d-11-devices-downlevel-intro">feature level</a> at which you create the rendering device.

### -param height

Type: <b><a href="/windows/desktop/WinProg/windows-data-types">UINT</a></b>

Texture height (in texels). The  range is from 1 to D3D11_REQ_TEXTURE2D_U_OR_V_DIMENSION (16384). For a texture cube-map, the  range is from 1 to D3D11_REQ_TEXTURECUBE_DIMENSION (16384). However, the range is actually constrained by the <a href="/windows/desktop/direct3d11/overviews-direct3d-11-devices-downlevel-intro">feature level</a> at which you create the rendering device.

### -param arraySize

Type: <b><a href="/windows/desktop/WinProg/windows-data-types">UINT</a></b>

Number of textures in the texture array. The  range is from 1 to D3D11_REQ_TEXTURE2D_ARRAY_AXIS_DIMENSION (2048). For a texture cube-map, this value is a multiple of 6 (that is, 6 times the value in the <b>NumCubes</b> member of <a href="/windows/desktop/api/d3d11/ns-d3d11-d3d11_texcube_array_srv">D3D11_TEXCUBE_ARRAY_SRV</a>), and the  range is from 6 to 2046. The range is actually constrained by the <a href="/windows/desktop/direct3d11/overviews-direct3d-11-devices-downlevel-intro">feature level</a> at which you create the rendering device.

### -param mipLevels

Type: <b><a href="/windows/desktop/WinProg/windows-data-types">UINT</a></b>

The maximum number of mipmap levels in the texture. See the remarks in <a href="/windows/desktop/api/d3d11/ns-d3d11-d3d11_tex1d_srv">D3D11_TEX1D_SRV</a>. Use 1 for a multisampled texture; or 0 to generate a full set of subtextures.

### -param bindFlags

Type: <b><a href="/windows/desktop/WinProg/windows-data-types">UINT</a></b>

A combination of <a href="/windows/desktop/api/d3d11/ne-d3d11-d3d11_bind_flag">D3D11_BIND_FLAG</a>-typed values that are combined by using a bitwise OR operation. The resulting value specifies how to bind the texture to pipeline stages.

### -param usage

Type: <b><a href="/windows/desktop/api/d3d11/ne-d3d11-d3d11_usage">D3D11_USAGE</a></b>

A <a href="/windows/desktop/api/d3d11/ne-d3d11-d3d11_usage">D3D11_USAGE</a>-typed value that identifies how the texture is to be read from and written to.

### -param cpuaccessFlags

Type: <b><a href="/windows/desktop/WinProg/windows-data-types">UINT</a></b>

A combination of <a href="/windows/desktop/api/d3d11/ne-d3d11-d3d11_cpu_access_flag">D3D11_CPU_ACCESS_FLAG</a>-typed values that are combined by using a bitwise OR operation. The resulting value specifies the types of CPU access allowed.

### -param sampleCount

Type: <b><a href="/windows/desktop/WinProg/windows-data-types">UINT</a></b>

The sample count.

### -param sampleQuality

Type: <b><a href="/windows/desktop/WinProg/windows-data-types">UINT</a></b>

The sample quality.

### -param miscFlags

Type: <b><a href="/windows/desktop/WinProg/windows-data-types">UINT</a></b>

A combination of <a href="/windows/desktop/api/d3d11/ne-d3d11-d3d11_resource_misc_flag">D3D11_RESOURCE_MISC_FLAG</a>-typed values that are combined by using a bitwise OR operation. The resulting value identifies other, less common resource options. For a texture cube-map, set the <a href="/windows/desktop/api/d3d11/ne-d3d11-d3d11_resource_misc_flag">D3D11_RESOURCE_MISC_TEXTURECUBE</a> flag. Cube-map arrays (that is, <i>arraySize</i> &gt; 6) require feature level <a href="/windows/desktop/api/d3dcommon/ne-d3dcommon-d3d_feature_level">D3D_FEATURE_LEVEL_10_1</a> or higher.

## -see-also

<a href="/previous-versions/windows/desktop/legacy/jj151700(v=vs.85)">CD3D11_TEXTURE2D_DESC</a>