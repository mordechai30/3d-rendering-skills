Source: [https://learn.microsoft.com/en-us/windows/win32/direct3d11/how-to--use-dynamic-resources](<https://learn.microsoft.com/en-us/windows/win32/direct3d11/how-to--use-dynamic-resources>)

# How to: Use dynamic resources

**Important APIs**

-   [**ID3D11DeviceContext::Map**](./nf-d3d11-id3d11devicecontext-map-d6df2a4196.md)
-   [**ID3D11DeviceContext::Unmap**](./nf-d3d11-id3d11devicecontext-unmap-6abfb49544.md)
-   [**D3D11\_USAGE**](./ne-d3d11-d3d11_usage-8197affe09.md)

You create and use dynamic resources when your app needs to change data in those resources. You can create textures and buffers for dynamic usage.

## What you need to know

### Technologies

-   [How to: Create a Texture](./overviews-direct3d-11-resources-textures-create-455a451604.md)
-   [How to: Initialize a Texture Programmatically](./overviews-direct3d-11-resources-textures-how-to-fill-manually-d1492474a7.md)
-   [How to: Create a Constant Buffer](./overviews-direct3d-11-resources-buffers-constant-how-to-cc243a75d3.md)

### Prerequisites

We assume that you are familiar with C++. You also need basic experience with graphics programming concepts.

## Instructions

### Step 1: Specify dynamic usage

If you want your app to be able to make changes to resources, you must specify those resources as dynamic and writable when you create them.

**To specify dynamic usage**

1.  Specify the resource usage as dynamic. For example, specify the [**D3D11\_USAGE\_DYNAMIC**](./ne-d3d11-d3d11_usage-8197affe09.md) value in the **Usage** member of [**D3D11\_BUFFER\_DESC**](./ns-d3d11-d3d11_buffer_desc-dbbb31b85c.md) for a vertex or constant buffer and specify the **D3D11\_USAGE\_DYNAMIC** value in the **Usage** member of [**D3D11\_TEXTURE2D\_DESC**](./ns-d3d11-d3d11_texture2d_desc-f26127b311.md) for a 2D texture.
2.  Specify the resource as writable. For example, specify the [**D3D11\_CPU\_ACCESS\_WRITE**](./ne-d3d11-d3d11_cpu_access_flag-2c51d58b52.md) value in the **CPUAccessFlags** member of [**D3D11\_BUFFER\_DESC**](./ns-d3d11-d3d11_buffer_desc-dbbb31b85c.md) or [**D3D11\_TEXTURE2D\_DESC**](./ns-d3d11-d3d11_texture2d_desc-f26127b311.md).
3.  Pass the resource description to the creation function. For example, pass the address of [**D3D11\_BUFFER\_DESC**](./ns-d3d11-d3d11_buffer_desc-dbbb31b85c.md) to [**ID3D11Device::CreateBuffer**](./nf-d3d11-id3d11device-createbuffer-973d575f5e.md) and pass the address of [**D3D11\_TEXTURE2D\_DESC**](./ns-d3d11-d3d11_texture2d_desc-f26127b311.md) to [**ID3D11Device::CreateTexture2D**](./nf-d3d11-id3d11device-createtexture2d-39a4608b7c.md).

Here is an example of creating a dynamic vertex buffer:


```C++
    // Create a vertex buffer for a triangle.

    float2 triangleVertices[] =
    {
        float2(-0.5f, -0.5f),
        float2(0.0f, 0.5f),
        float2(0.5f, -0.5f),
    };

    D3D11_BUFFER_DESC vertexBufferDesc = { 0 };
    vertexBufferDesc.ByteWidth = sizeof(float2)* ARRAYSIZE(triangleVertices);
    vertexBufferDesc.Usage = D3D11_USAGE_DYNAMIC;
    vertexBufferDesc.BindFlags = D3D11_BIND_VERTEX_BUFFER;
    vertexBufferDesc.CPUAccessFlags = D3D11_CPU_ACCESS_WRITE;
    vertexBufferDesc.MiscFlags = 0;
    vertexBufferDesc.StructureByteStride = 0;

    D3D11_SUBRESOURCE_DATA vertexBufferData;
    vertexBufferData.pSysMem = triangleVertices;
    vertexBufferData.SysMemPitch = 0;
    vertexBufferData.SysMemSlicePitch = 0;

    DX::ThrowIfFailed(
        m_d3dDevice->CreateBuffer(
        &vertexBufferDesc,
        &vertexBufferData,
        &vertexBuffer2
        )
        );

```



### Step 2: Change a dynamic resource

If you specified a resource as dynamic and writable when you created it, you can later make changes to that resource.

**To change data in a dynamic resource**

1.  Set up the new data for the resource. Declare a [**D3D11\_MAPPED\_SUBRESOURCE**](./ns-d3d11-d3d11_mapped_subresource-5dbbf0bcb8.md) type variable and initialize it to zero. You'll use this variable to change the resource.
2.  Disable graphics processing unit (GPU) access to the data that you want to change and get a pointer to the memory that contains the data. To get this pointer, pass [**D3D11\_MAP\_WRITE\_DISCARD**](./ne-d3d11-d3d11_map-80dcff5b4f.md) to the *MapType* parameter when you call [**ID3D11DeviceContext::Map**](./nf-d3d11-id3d11devicecontext-map-d6df2a4196.md). Set this pointer to the address of the [**D3D11\_MAPPED\_SUBRESOURCE**](./ns-d3d11-d3d11_mapped_subresource-5dbbf0bcb8.md) variable from the previous step.
3.  Write the new data to the memory.
4.  Call [**ID3D11DeviceContext::Unmap**](./nf-d3d11-id3d11devicecontext-unmap-6abfb49544.md) to reenable GPU access to the data when you're finished writing the new data.

Here is an example of changing a dynamic vertex buffer:


```C++
// This might get called as the result of a click event to double the size of the triangle.
void TriangleRenderer::MapDoubleVertices()
{
    D3D11_MAPPED_SUBRESOURCE mappedResource;
    ZeroMemory(&mappedResource, sizeof(D3D11_MAPPED_SUBRESOURCE));
    float2 vertices[] =
    {
        float2(-1.0f, -1.0f),
        float2(0.0f, 1.0f),
        float2(1.0f, -1.0f),
    };
    //  Disable GPU access to the vertex buffer data.
    auto m_d3dContext = m_deviceResources->GetD3DDeviceContext();
    m_d3dContext->Map(vertexBuffer2.Get(), 0, D3D11_MAP_WRITE_DISCARD, 0, &mappedResource);
    //  Update the vertex buffer here.
    memcpy(mappedResource.pData, vertices, sizeof(vertices));
    //  Reenable GPU access to the vertex buffer data.
    m_d3dContext->Unmap(vertexBuffer2.Get(), 0);
}
```



## Remarks

### Using dynamic textures

We recommend that you create only one dynamic texture per format and possibly per size. We don't recommend creating dynamic mipmaps, cubes, and volumes because of the additional overhead in mapping every level. For mipmaps, you can specify [**D3D11\_MAP\_WRITE\_DISCARD**](./ne-d3d11-d3d11_map-80dcff5b4f.md) only on the top level. All levels are discarded by mapping just the top level. This behavior is the same for volumes and cubes. For cubes, the top level and face 0 are mapped.

### Using dynamic buffers

When you call [**Map**](./nf-d3d11-id3d11devicecontext-map-d6df2a4196.md) on a static vertex buffer while the GPU is using the buffer, you get a significant performance penalty. In this situation, **Map** must wait until the GPU is finished reading vertex or index data from the buffer before **Map** can return to the calling app, which causes a significant delay. Calling **Map** and then rendering from a static buffer several times per frame also prevents the GPU from buffering rendering commands because it must finish commands before returning the map pointer. Without buffered commands, the GPU remains idle until after the app is finished filling the vertex buffer or index buffer and issues a rendering command.

Ideally the vertex or index data would never change, but this is not always possible. There are many situations where the app needs to change vertex or index data every frame, perhaps even multiple times per frame. For these situations, we recommend that you create the vertex or index buffer with [**D3D11\_USAGE\_DYNAMIC**](./ne-d3d11-d3d11_usage-8197affe09.md). This usage flag causes the runtime to optimize for frequent map operations. **D3D11\_USAGE\_DYNAMIC** is only useful when the buffer is mapped frequently; if data is to remain constant, place that data in a static vertex or index buffer.

To receive a performance improvement when you use dynamic vertex buffers, your app must call [**Map**](./nf-d3d11-id3d11devicecontext-map-d6df2a4196.md) with the appropriate [**D3D11\_MAP**](./ne-d3d11-d3d11_map-80dcff5b4f.md) values. [**D3D11\_MAP\_WRITE\_DISCARD**](./ne-d3d11-d3d11_map-80dcff5b4f.md) indicates that the app doesn't need to keep the old vertex or index data in the buffer. If the GPU is still using the buffer when you call **Map** with **D3D11\_MAP\_WRITE\_DISCARD**, the runtime returns a pointer to a new region of memory instead of the old buffer data. This allows the GPU to continue using the old data while the app places data in the new buffer. No additional memory management is required in the app; the old buffer is reused or destroyed automatically when the GPU is finished with it.

> [!Note]  
> When you map a buffer with [**D3D11\_MAP\_WRITE\_DISCARD**](./ne-d3d11-d3d11_map-80dcff5b4f.md), the runtime always discards the entire buffer. You can't preserve info in unmapped areas of the buffer by specifying a nonzero offset or limited size field.

 

There are cases where the amount of data the app needs to store per map is small, such as adding four vertices to render a sprite. [**D3D11\_MAP\_WRITE\_NO\_OVERWRITE**](./ne-d3d11-d3d11_map-80dcff5b4f.md) indicates that the app will not overwrite data already in use in the dynamic buffer. The [**Map**](./nf-d3d11-id3d11devicecontext-map-d6df2a4196.md) call will return a pointer to the old data, which will allow the app to add new data in unused regions of the vertex or index buffer. The app must not modify vertices or indices that are used in a draw operation as they might still be in use by the GPU. We recommend that the app then use [**D3D11\_MAP\_WRITE\_DISCARD**](./ne-d3d11-d3d11_map-80dcff5b4f.md) after the dynamic buffer is full to receive a new region of memory, which discards the old vertex or index data after the GPU is finished.

The asynchronous query mechanism is useful to determine if vertices are still in use by the GPU. Issue a query of type [**D3D11\_QUERY\_EVENT**](./ne-d3d11-d3d11_query-b039f0327f.md) after the last draw call that uses the vertices. The vertices are no longer in use when [**ID3D11DeviceContext::GetData**](./nf-d3d11-id3d11devicecontext-getdata-3fb2bae12b.md) returns S\_OK. When you map a buffer with [**D3D11\_MAP\_WRITE\_DISCARD**](./ne-d3d11-d3d11_map-80dcff5b4f.md) or no map values, you are always guaranteed that the vertices are synchronized properly with the GPU. But, when you map without map values, you will incur the performance penalty described earlier.

> [!Note]  
> The Direct3D 11.1 runtime, which is available starting with Windows 8, enables mapping dynamic constant buffers and shader resource views (SRVs) of dynamic buffers with [**D3D11\_MAP\_WRITE\_NO\_OVERWRITE**](./ne-d3d11-d3d11_map-80dcff5b4f.md). The Direct3D 11 and earlier runtimes limited no-overwrite partial-update mapping to vertex or index buffers. To determine if a Direct3D device supports these features, call [**ID3D11Device::CheckFeatureSupport**](./nf-d3d11-id3d11device-checkfeaturesupport-ec5826ac8e.md) with [**D3D11\_FEATURE\_D3D11\_OPTIONS**](./ne-d3d11-d3d11_feature-a05a7560bc.md). **CheckFeatureSupport** fills members of a [**D3D11\_FEATURE\_DATA\_D3D11\_OPTIONS**](./ns-d3d11-d3d11_feature_data_d3d11_options-844c1460d6.md) structure with the device's features. The relevant members here are **MapNoOverwriteOnDynamicConstantBuffer** and **MapNoOverwriteOnDynamicBufferSRV**.

 

## Related topics

<dl> <dt>

[How to Use Direct3D 11](./how-to-use-direct3d-11-112ea0ccbf.md)
</dt> </dl>