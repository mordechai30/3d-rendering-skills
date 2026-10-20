Source: [https://learn.microsoft.com/en-us/windows/win32/api/d3d11/nf-d3d11-cd3d11_texture3d_desc-cd3d11_texture3d_desc(dxgi_format_uint_uint_uint_uint_uint_d3d11_usage_uint_uint)](<https://learn.microsoft.com/en-us/windows/win32/api/d3d11/nf-d3d11-cd3d11_texture3d_desc-cd3d11_texture3d_desc(dxgi_format_uint_uint_uint_uint_uint_d3d11_usage_uint_uint)>)

# CD3D11_TEXTURE3D_DESC::CD3D11_TEXTURE3D_DESC(DXGI_FORMAT,UINT,UINT,UINT,UINT,UINT,D3D11_USAGE,UINT,UINT)


## -description

Instantiates a new instance of a <a href="/previous-versions/windows/desktop/legacy/jj151706(v=vs.85)">CD3D11_TEXTURE3D_DESC</a> structure that is initialized with <a href="/windows/desktop/api/d3d11/ns-d3d11-d3d11_texture3d_desc">D3D11_TEXTURE3D_DESC</a> values.

## -parameters

### -param format

Type: <b><a href="/windows/desktop/api/dxgiformat/ne-dxgiformat-dxgi_format">DXGI_FORMAT</a></b>

A <a href="/windows/desktop/api/dxgiformat/ne-dxgiformat-dxgi_format">DXGI_FORMAT</a>-typed value that specifies the texture format.

### -param width

Type: <b><a href="/windows/desktop/WinProg/windows-data-types">UINT</a></b>

Texture width (in texels). The  range is from 1 to D3D11_REQ_TEXTURE3D_U_V_OR_W_DIMENSION (2048). However, the range is actually constrained by the <a href="/windows/desktop/direct3d11/overviews-direct3d-11-devices-downlevel-intro">feature level</a> at which you create the rendering device.

### -param height

Type: <b><a href="/windows/desktop/WinProg/windows-data-types">UINT</a></b>

Texture height (in texels). The  range is from 1 to D3D11_REQ_TEXTURE3D_U_V_OR_W_DIMENSION (2048). However, the range is actually constrained by the <a href="/windows/desktop/direct3d11/overviews-direct3d-11-devices-downlevel-intro">feature level</a> at which you create the rendering device.

### -param depth

Type: <b><a href="/windows/desktop/WinProg/windows-data-types">UINT</a></b>

Texture depth (in texels). The  range is from 1 to D3D11_REQ_TEXTURE3D_U_V_OR_W_DIMENSION (2048). However, the range is actually constrained by the <a href="/windows/desktop/direct3d11/overviews-direct3d-11-devices-downlevel-intro">feature level</a> at which you create the rendering device.

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

### -param miscFlags

Type: <b><a href="/windows/desktop/WinProg/windows-data-types">UINT</a></b>

A combination of <a href="/windows/desktop/api/d3d11/ne-d3d11-d3d11_resource_misc_flag">D3D11_RESOURCE_MISC_FLAG</a>-typed values that are combined by using a bitwise OR operation. The resulting value identifies other, less common resource options.

## -see-also

<a href="/previous-versions/windows/desktop/legacy/jj151706(v=vs.85)">CD3D11_TEXTURE3D_DESC</a>