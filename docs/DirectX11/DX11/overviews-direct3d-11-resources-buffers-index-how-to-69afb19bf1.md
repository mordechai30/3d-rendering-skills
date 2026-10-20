Source: [https://learn.microsoft.com/en-us/windows/win32/direct3d11/overviews-direct3d-11-resources-buffers-index-how-to](<https://learn.microsoft.com/en-us/windows/win32/direct3d11/overviews-direct3d-11-resources-buffers-index-how-to>)

# How to: Create an Index Buffer

[Index buffers](./overviews-direct3d-11-resources-buffers-intro-8b0955efd2.md) contain index data. This topic shows how to initialize an [index buffer](./overviews-direct3d-11-resources-buffers-intro-8b0955efd2.md) in preparation for rendering.

**To initialize an index buffer**

1.  Create a buffer that contains your index information.
2.  Create a buffer description by filling in a [**D3D11\_BUFFER\_DESC**](./ns-d3d11-d3d11_buffer_desc-dbbb31b85c.md) structure. Pass the D3D11\_BIND\_INDEX\_BUFFER flag to the **BindFlags** member and pass the size of the buffer in bytes to the **ByteWidth** member.
3.  Create a subresource data description by filling in a [**D3D11\_SUBRESOURCE\_DATA**](./ns-d3d11-d3d11_subresource_data-0227c25259.md) structure. The **pSysMem** member should point directly to the index data created in step one.
4.  Call [**ID3D11Device::CreateBuffer**](./nf-d3d11-id3d11device-createbuffer-973d575f5e.md) while passing the [**D3D11\_BUFFER\_DESC**](./ns-d3d11-d3d11_buffer_desc-dbbb31b85c.md) structure, the [**D3D11\_SUBRESOURCE\_DATA**](./ns-d3d11-d3d11_subresource_data-0227c25259.md) structure, and the address of a pointer to the [**ID3D11Buffer**](./nn-d3d11-id3d11buffer-0e4ba9908b.md) interface to initialize.

The following code example demonstrates how to create an index buffer. This example assumes that


```
g_pd3dDevice
```



is a valid [**ID3D11Device**](./nn-d3d11-id3d11device-6e49ef4b9e.md) object and that


```
g_pd3dContext
```



is a valid [**ID3D11DeviceContext**](./nn-d3d11-id3d11devicecontext-abe911f651.md) object.


```
ID3D11Buffer *g_pIndexBuffer = NULL;

// Create indices.
unsigned int indices[] = { 0, 1, 2 };

// Fill in a buffer description.
D3D11_BUFFER_DESC bufferDesc;
bufferDesc.Usage           = D3D11_USAGE_DEFAULT;
bufferDesc.ByteWidth       = sizeof( unsigned int ) * 3;
bufferDesc.BindFlags       = D3D11_BIND_INDEX_BUFFER;
bufferDesc.CPUAccessFlags  = 0;
bufferDesc.MiscFlags       = 0;

// Define the resource data.
D3D11_SUBRESOURCE_DATA InitData;
InitData.pSysMem = indices;
InitData.SysMemPitch = 0;
InitData.SysMemSlicePitch = 0;

// Create the buffer with the device.
hr = g_pd3dDevice->CreateBuffer( &bufferDesc, &InitData, &g_pIndexBuffer );
if( FAILED( hr ) )
    return hr;

// Set the buffer.
g_pd3dContext->IASetIndexBuffer( g_pIndexBuffer, DXGI_FORMAT_R32_UINT, 0 );
    
```



## Related topics

<dl> <dt>

[Buffers](./overviews-direct3d-11-resources-buffers-1faa07e5b1.md)
</dt> <dt>

[How to Use Direct3D 11](./how-to-use-direct3d-11-112ea0ccbf.md)
</dt> </dl>