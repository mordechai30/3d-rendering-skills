Source: [https://learn.microsoft.com/en-us/windows/win32/direct3d11/overviews-direct3d-11-resources-textures-create](<https://learn.microsoft.com/en-us/windows/win32/direct3d11/overviews-direct3d-11-resources-textures-create>)

# How to: Create a Texture

The simplest way to create a texture is to describe its properties and call the texture creation API. This topic shows how to create a texture.

**To create a texture**

1.  Fill in a [**D3D11\_TEXTURE2D\_DESC**](./ns-d3d11-d3d11_texture2d_desc-f26127b311.md) structure with a description of the texture parameters.
2.  Create the texture by calling [**ID3D11Device::CreateTexture2D**](./nf-d3d11-id3d11device-createtexture2d-39a4608b7c.md) with the texture description.

This example creates a 256 x 256 texture, with [**dynamic usage**](./ne-d3d11-d3d11_usage-8197affe09.md), for use as a [**shader resource**](./ne-d3d11-d3d11_bind_flag-78d4ee3d0d.md) with [**cpu write access**](./ne-d3d11-d3d11_cpu_access_flag-2c51d58b52.md).


```
D3D11_TEXTURE2D_DESC desc;
desc.Width = 256;
desc.Height = 256;
desc.MipLevels = desc.ArraySize = 1;
desc.Format = DXGI_FORMAT_R8G8B8A8_UNORM;
desc.SampleDesc.Count = 1;
desc.Usage = D3D11_USAGE_DYNAMIC;
desc.BindFlags = D3D11_BIND_SHADER_RESOURCE;
desc.CPUAccessFlags = D3D11_CPU_ACCESS_WRITE;
desc.MiscFlags = 0;

ID3D11Device *pd3dDevice; // Don't forget to initialize this
ID3D11Texture2D *pTexture = NULL;
pd3dDevice->CreateTexture2D( &desc, NULL, &pTexture );
```



## Related topics

<dl> <dt>

[How to Use Direct3D 11](./how-to-use-direct3d-11-112ea0ccbf.md)
</dt> <dt>

[Textures](./overviews-direct3d-11-resources-textures-6654061a52.md)
</dt> </dl>