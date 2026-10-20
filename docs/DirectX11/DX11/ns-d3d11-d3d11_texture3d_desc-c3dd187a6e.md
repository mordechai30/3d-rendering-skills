Source: [https://learn.microsoft.com/en-us/windows/win32/api/D3D11/ns-d3d11-d3d11_texture3d_desc](<https://learn.microsoft.com/en-us/windows/win32/api/D3D11/ns-d3d11-d3d11_texture3d_desc>)

# D3D11_TEXTURE3D_DESC structure


## -description

Describes a 3D texture.

## -struct-fields

### -field Width

Type: <b><a href="/windows/desktop/WinProg/windows-data-types">UINT</a></b>

Texture width (in texels). The  range is from 1 to D3D11_REQ_TEXTURE3D_U_V_OR_W_DIMENSION (2048). However, the range is actually constrained by the <a href="/windows/desktop/direct3d11/overviews-direct3d-11-devices-downlevel-intro">feature level</a> at which you create the rendering device. For more information about restrictions, see Remarks.

### -field Height

Type: <b><a href="/windows/desktop/WinProg/windows-data-types">UINT</a></b>

Texture height (in texels). The  range is from 1 to D3D11_REQ_TEXTURE3D_U_V_OR_W_DIMENSION (2048). However, the range is actually constrained by the <a href="/windows/desktop/direct3d11/overviews-direct3d-11-devices-downlevel-intro">feature level</a> at which you create the rendering device. For more information about restrictions, see Remarks.

### -field Depth

Type: <b><a href="/windows/desktop/WinProg/windows-data-types">UINT</a></b>

Texture depth (in texels). The  range is from 1 to D3D11_REQ_TEXTURE3D_U_V_OR_W_DIMENSION (2048). However, the range is actually constrained by the <a href="/windows/desktop/direct3d11/overviews-direct3d-11-devices-downlevel-intro">feature level</a> at which you create the rendering device. For more information about restrictions, see Remarks.

### -field MipLevels

Type: <b><a href="/windows/desktop/WinProg/windows-data-types">UINT</a></b>

The maximum number of mipmap levels in the texture. See the remarks in <a href="/windows/desktop/api/d3d11/ns-d3d11-d3d11_tex1d_srv">D3D11_TEX1D_SRV</a>. Use 1 for a multisampled texture; or 0 to generate a full set of subtextures.

### -field Format

Type: <b><a href="/windows/desktop/api/dxgiformat/ne-dxgiformat-dxgi_format">DXGI_FORMAT</a></b>

Texture format (see <a href="/windows/desktop/api/dxgiformat/ne-dxgiformat-dxgi_format">DXGI_FORMAT</a>).

### -field Usage

Type: <b><a href="/windows/desktop/api/d3d11/ne-d3d11-d3d11_usage">D3D11_USAGE</a></b>

Value that identifies how the texture is to be read from and written to. The most common value is D3D11_USAGE_DEFAULT; see <a href="/windows/desktop/api/d3d11/ne-d3d11-d3d11_usage">D3D11_USAGE</a> for all possible values.

### -field BindFlags

Type: <b><a href="/windows/desktop/WinProg/windows-data-types">UINT</a></b>

Flags (see <a href="/windows/desktop/api/d3d11/ne-d3d11-d3d11_bind_flag">D3D11_BIND_FLAG</a>) for binding to pipeline stages. The flags can be combined by a bitwise OR.

### -field CPUAccessFlags

Type: <b><a href="/windows/desktop/WinProg/windows-data-types">UINT</a></b>

Flags (see <a href="/windows/desktop/api/d3d11/ne-d3d11-d3d11_cpu_access_flag">D3D11_CPU_ACCESS_FLAG</a>) to specify the types of CPU access allowed. Use 0 if CPU access is not required. These flags can be combined with a bitwise OR.

### -field MiscFlags

Type: <b><a href="/windows/desktop/WinProg/windows-data-types">UINT</a></b>

Flags (see <a href="/windows/desktop/api/d3d11/ne-d3d11-d3d11_resource_misc_flag">D3D11_RESOURCE_MISC_FLAG</a>) that identify other, less common resource options. Use 0 if none of these flags apply. These flags can be combined with a bitwise OR.

## -remarks

This structure is used in a call to <a href="/windows/desktop/api/d3d11/nf-d3d11-id3d11device-createtexture3d">ID3D11Device::CreateTexture3D</a>.

In addition to this structure, you can also use the <a href="/previous-versions/windows/desktop/legacy/jj151706(v=vs.85)">CD3D11_TEXTURE3D_DESC</a> derived structure, which is defined  in D3D11.h and behaves like an inherited class, to help create a texture description.

The device restricts the size of subsampled, block compressed, and bit format resources to be multiples of sizes specific to each format.

The texture size range is determined by the <a href="/windows/desktop/direct3d11/overviews-direct3d-11-devices-downlevel-intro">feature level</a> at which you create the device and not the Microsoft Direct3D interface version. For example, if you use Microsoft Direct3D 10 hardware at feature level 10 (<a href="/windows/desktop/api/d3dcommon/ne-d3dcommon-d3d_feature_level">D3D_FEATURE_LEVEL_10_0</a>) and call <a href="/windows/desktop/api/d3d11/nf-d3d11-d3d11createdevice">D3D11CreateDevice</a> to create an <a href="/windows/desktop/api/d3d11/nn-d3d11-id3d11device">ID3D11Device</a>, you must constrain the maximum texture size to D3D10_REQ_TEXTURE3D_U_V_OR_W_DIMENSION (2048) when you create your 3D texture.

## -see-also

<a href="/windows/desktop/direct3d11/d3d11-graphics-reference-resource-structures">Resource Structures</a>