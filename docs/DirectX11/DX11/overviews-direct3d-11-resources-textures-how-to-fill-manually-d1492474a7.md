Source: [https://learn.microsoft.com/en-us/windows/win32/direct3d11/overviews-direct3d-11-resources-textures-how-to-fill-manually](<https://learn.microsoft.com/en-us/windows/win32/direct3d11/overviews-direct3d-11-resources-textures-how-to-fill-manually>)

# How to: Initialize a Texture Programmatically

You can initialize a texture during object creation, or you can fill the object programmatically after it is created. This topic has several examples showing how to initialize textures that are created with different types of usages. This example assumes you already know how to [Create a Texture](./overviews-direct3d-11-resources-textures-create-455a451604.md).

-   [Default Usage](#default-usage)
-   [Dynamic Usage](#dynamic-usage)
-   [Staging Usage](#staging-usage)
-   [Related topics](#related-topics)

## Default Usage

The most common type of usage is default usage. To fill a default texture (one created with **D3D11\_USAGE\_DEFAULT**) you can either:

-   Call [**ID3D11Device::CreateTexture2D**](./nf-d3d11-id3d11device-createtexture2d-39a4608b7c.md) and initialize *pInitialData* to point to data provided from an application.

    or

-   After calling [**ID3D11Device::CreateTexture2D**](./nf-d3d11-id3d11device-createtexture2d-39a4608b7c.md), use [**ID3D11DeviceContext::UpdateSubresource**](./nf-d3d11-id3d11devicecontext-updatesubresource-0caec3c0c2.md) to fill the default texture with data from a pointer provided by the application.

## Dynamic Usage

To fill a dynamic texture (one created with **D3D11\_USAGE\_DYNAMIC**):

1.  Get a pointer to the texture memory by passing in **D3D11\_MAP\_WRITE\_DISCARD** when calling [**ID3D11DeviceContext::Map**](./nf-d3d11-id3d11devicecontext-map-d6df2a4196.md).
2.  Write data to the memory.
3.  Call [**ID3D11DeviceContext::Unmap**](./nf-d3d11-id3d11devicecontext-unmap-6abfb49544.md) when you are finished writing data.

## Staging Usage

To fill a staging texture (one created with **D3D11\_USAGE\_STAGING**):

1.  Get a pointer to the texture memory by passing in **D3D11\_MAP\_WRITE** when calling [**ID3D11DeviceContext::Map**](./nf-d3d11-id3d11devicecontext-map-d6df2a4196.md).
2.  Write data to the memory.
3.  Call [**ID3D11DeviceContext::Unmap**](./nf-d3d11-id3d11devicecontext-unmap-6abfb49544.md) when you are finished writing data.

A staging texture can then be used as the source parameter to [**ID3D11DeviceContext::CopyResource**](./nf-d3d11-id3d11devicecontext-copyresource-049b96d8b1.md) or [**ID3D11DeviceContext::CopySubresourceRegion**](./nf-d3d11-id3d11devicecontext-copysubresourceregion-1d93555d33.md) to fill a default or dynamic resource.

## Related topics

<dl> <dt>

[How to Use Direct3D 11](./how-to-use-direct3d-11-112ea0ccbf.md)
</dt> <dt>

[Textures](./overviews-direct3d-11-resources-textures-6654061a52.md)
</dt> </dl>