Source: [https://learn.microsoft.com/en-us/windows/win32/direct3d11/overviews-direct3d-11-resources-buffers-vertex-how-to](<https://learn.microsoft.com/en-us/windows/win32/direct3d11/overviews-direct3d-11-resources-buffers-vertex-how-to>)

# How to: Create a Vertex Buffer

[Vertex buffers](./overviews-direct3d-11-resources-buffers-intro-8b0955efd2.md) contain per vertex data. This topic shows how to initialize a static [vertex buffer](./overviews-direct3d-11-resources-buffers-intro-8b0955efd2.md), that is, a vertex buffer that does not change. For help initializing a non-static buffer, see the [remarks](#remarks) section.

**To initialize a static vertex buffer**

1.  Define a structure that describes a vertex. For example, if your vertex data contains position data and color data, your structure would have one vector that describes the position and another that describes the color.
2.  Allocate memory (using malloc or new) for the structure that you defined in step one. Fill this buffer with the actual vertex data that describes your geometry.
3.  Create a buffer description by filling in a [**D3D11\_BUFFER\_DESC**](./ns-d3d11-d3d11_buffer_desc-dbbb31b85c.md) structure. Pass the D3D11\_BIND\_VERTEX\_BUFFER flag to the **BindFlags** member and pass the size of the structure from step one to the **ByteWidth** member.
4.  Create a subresource data description by filling in a [**D3D11\_SUBRESOURCE\_DATA**](./ns-d3d11-d3d11_subresource_data-0227c25259.md) structure. The **pSysMem** member of the [**D3D11\_SUBRESOURCE\_DATA**](./ns-d3d11-d3d11_subresource_data-0227c25259.md) structure should point directly to the resource data created in step two.
5.  Call [**ID3D11Device::CreateBuffer**](./nf-d3d11-id3d11device-createbuffer-973d575f5e.md) while passing the [**D3D11\_BUFFER\_DESC**](./ns-d3d11-d3d11_buffer_desc-dbbb31b85c.md) structure, the [**D3D11\_SUBRESOURCE\_DATA**](./ns-d3d11-d3d11_subresource_data-0227c25259.md) structure, and the address of a pointer to the [**ID3D11Buffer**](./nn-d3d11-id3d11buffer-0e4ba9908b.md) interface to initialize.

The following code example demonstrates how to create a vertex buffer. This example assumes that **g\_pd3dDevice** is a valid [**ID3D11Device**](./nn-d3d11-id3d11device-6e49ef4b9e.md) object.


```
ID3D11Buffer*      g_pVertexBuffer;

// Define the data-type that
// describes a vertex.
struct SimpleVertexCombined
{
    XMFLOAT3 Pos;  
    XMFLOAT3 Col;  
};

// Supply the actual vertex data.
SimpleVertexCombined verticesCombo[] =
{
    XMFLOAT3( 0.0f, 0.5f, 0.5f ),
    XMFLOAT3( 0.0f, 0.0f, 0.5f ),
    XMFLOAT3( 0.5f, -0.5f, 0.5f ),
    XMFLOAT3( 0.5f, 0.0f, 0.0f ),
    XMFLOAT3( -0.5f, -0.5f, 0.5f ),
    XMFLOAT3( 0.0f, 0.5f, 0.0f ),
};

// Fill in a buffer description.
D3D11_BUFFER_DESC bufferDesc;
bufferDesc.Usage            = D3D11_USAGE_DEFAULT;
bufferDesc.ByteWidth        = sizeof( SimpleVertexCombined ) * 3;
bufferDesc.BindFlags        = D3D11_BIND_VERTEX_BUFFER;
bufferDesc.CPUAccessFlags   = 0;
bufferDesc.MiscFlags        = 0;

// Fill in the subresource data.
D3D11_SUBRESOURCE_DATA InitData;
InitData.pSysMem = verticesCombo;
InitData.SysMemPitch = 0;
InitData.SysMemSlicePitch = 0;

// Create the vertex buffer.
hr = g_pd3dDevice->CreateBuffer( &bufferDesc, &InitData, &g_pVertexBuffer );
    
```



## Remarks

Here are some ways to initialize a vertex buffer that changes over time.

1.  Create a 2nd buffer with [**D3D11\_USAGE\_STAGING**](./ne-d3d11-d3d11_usage-8197affe09.md); fill the second buffer using [**ID3D11DeviceContext::Map**](./nf-d3d11-id3d11devicecontext-map-d6df2a4196.md), [**ID3D11DeviceContext::Unmap**](./nf-d3d11-id3d11devicecontext-unmap-6abfb49544.md); use [**ID3D11DeviceContext::CopyResource**](./nf-d3d11-id3d11devicecontext-copyresource-049b96d8b1.md) to copy from the staging buffer to the default buffer.
2.  Use [**ID3D11DeviceContext::UpdateSubresource**](./nf-d3d11-id3d11devicecontext-updatesubresource-0caec3c0c2.md) to copy data from memory.
3.  Create a buffer with [**D3D11\_USAGE\_DYNAMIC**](./ne-d3d11-d3d11_usage-8197affe09.md), and fill it with [**ID3D11DeviceContext::Map**](./nf-d3d11-id3d11devicecontext-map-d6df2a4196.md), [**ID3D11DeviceContext::Unmap**](./nf-d3d11-id3d11devicecontext-unmap-6abfb49544.md) (using the Discard and NoOverwrite flags appropriately).

\#1 and \#2 are useful for content that changes less than once per frame. In general, GPU reads will be fast and CPU updates will be slower.

\#3 is useful for content that changes more than once per frame. In general, GPU reads will be slower, but CPU updates will be faster.

## Related topics

<dl> <dt>

[Buffers](./overviews-direct3d-11-resources-buffers-1faa07e5b1.md)
</dt> <dt>

[How to Use Direct3D 11](./how-to-use-direct3d-11-112ea0ccbf.md)
</dt> </dl>