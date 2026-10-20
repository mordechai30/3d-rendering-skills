Source: [https://learn.microsoft.com/en-us/windows/win32/api/D3D11/nf-d3d11-id3d11devicecontext-generatemips](<https://learn.microsoft.com/en-us/windows/win32/api/D3D11/nf-d3d11-id3d11devicecontext-generatemips>)

# ID3D11DeviceContext::GenerateMips


## -description

Generates mipmaps for the given shader resource.

## -parameters

### -param pShaderResourceView [in]

Type: <b><a href="/windows/desktop/api/d3d11/nn-d3d11-id3d11shaderresourceview">ID3D11ShaderResourceView</a>*</b>

A pointer to an <a href="/windows/desktop/api/d3d11/nn-d3d11-id3d11shaderresourceview">ID3D11ShaderResourceView</a> interface that represents the shader resource.

## -remarks

You can call <b>GenerateMips</b> on any shader-resource view to generate the lower mipmap levels for the shader resource. <b>GenerateMips</b> uses the largest mipmap level of the view to recursively generate the lower levels of the mip and stops with the smallest level that is specified by the view. If the base resource wasn't created with <a href="/windows/desktop/api/d3d11/ne-d3d11-d3d11_bind_flag">D3D11_BIND_RENDER_TARGET</a>, <a href="/windows/desktop/api/d3d11/ne-d3d11-d3d11_bind_flag">D3D11_BIND_SHADER_RESOURCE</a>, and <a href="/windows/desktop/api/d3d11/ne-d3d11-d3d11_resource_misc_flag">D3D11_RESOURCE_MISC_GENERATE_MIPS</a>, the call to <b>GenerateMips</b> has no effect.

<a href="/windows/desktop/direct3d11/overviews-direct3d-11-devices-downlevel-intro">Feature levels</a> 9.1, 9.2, and 9.3 can't support automatic generation of mipmaps for 3D (volume) textures.

Video adapters that support <a href="/windows/desktop/direct3d11/overviews-direct3d-11-devices-downlevel-intro">feature level</a> 9.1 and higher support generating mipmaps if you use any of these formats:


```

DXGI_FORMAT_R8G8B8A8_UNORM
DXGI_FORMAT_R8G8B8A8_UNORM_SRGB
DXGI_FORMAT_B5G6R5_UNORM
DXGI_FORMAT_B8G8R8A8_UNORM
DXGI_FORMAT_B8G8R8A8_UNORM_SRGB
DXGI_FORMAT_B8G8R8X8_UNORM
DXGI_FORMAT_B8G8R8X8_UNORM_SRGB

```


Video adapters that support <a href="/windows/desktop/direct3d11/overviews-direct3d-11-devices-downlevel-intro">feature level</a> 9.2 and higher support generating mipmaps if you use any of these formats in addition to any of the formats for feature level 9.1:


```

DXGI_FORMAT_R16G16B16A16_FLOAT
DXGI_FORMAT_R16G16B16A16_UNORM
DXGI_FORMAT_R16G16_FLOAT
DXGI_FORMAT_R16G16_UNORM
DXGI_FORMAT_R32_FLOAT

```


Video adapters that support <a href="/windows/desktop/direct3d11/overviews-direct3d-11-devices-downlevel-intro">feature level</a> 9.3 and higher support generating mipmaps if you use any of these formats in addition to any of the formats for feature levels 9.1 and 9.2:


```

DXGI_FORMAT_R32G32B32A32_FLOAT
DXGI_FORMAT_B4G4R4A4 (optional)

```


Video adapters that support <a href="/windows/desktop/direct3d11/overviews-direct3d-11-devices-downlevel-intro">feature level</a> 10 and higher support generating mipmaps if you use any of these formats in addition to any of the formats for feature levels 9.1, 9.2, and 9.3:


```

DXGI_FORMAT_R32G32B32_FLOAT (optional)
DXGI_FORMAT_R16G16B16A16_SNORM
DXGI_FORMAT_R32G32_FLOAT
DXGI_FORMAT_R10G10B10A2_UNORM
DXGI_FORMAT_R11G11B10_FLOAT
DXGI_FORMAT_R8G8B8A8_SNORM
DXGI_FORMAT_R16G16_SNORM
DXGI_FORMAT_R8G8_UNORM
DXGI_FORMAT_R8G8_SNORM
DXGI_FORMAT_R16_FLOAT
DXGI_FORMAT_R16_UNORM
DXGI_FORMAT_R16_SNORM
DXGI_FORMAT_R8_UNORM
DXGI_FORMAT_R8_SNORM
DXGI_FORMAT_A8_UNORM
DXGI_FORMAT_B5G5R5A1_UNORM (optional)

```


For all other unsupported formats, <b>GenerateMips</b> will silently fail.

## -see-also

<a href="/windows/desktop/api/dxgiformat/ne-dxgiformat-dxgi_format">DXGI_FORMAT</a>



<a href="/windows/desktop/api/d3d11/nn-d3d11-id3d11devicecontext">ID3D11DeviceContext</a>