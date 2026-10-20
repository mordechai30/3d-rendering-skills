Source: [https://learn.microsoft.com/en-us/windows/win32/direct3d11/overviews-direct3d-11-render-multi-thread-create](<https://learn.microsoft.com/en-us/windows/win32/direct3d11/overviews-direct3d-11-render-multi-thread-create>)

# Object Creation with Multithreading

Use the [**ID3D11Device**](./nn-d3d11-id3d11device-6e49ef4b9e.md) interface to create resources and objects, use the [**ID3D11DeviceContext**](./nn-d3d11-id3d11devicecontext-abe911f651.md) for [rendering](./overviews-direct3d-11-render-multi-thread-render-ae496f37e0.md).

Here are some examples of how to create resources:

-   [How to: Create a Vertex Buffer](./overviews-direct3d-11-resources-buffers-vertex-how-to-a34f96387c.md)
-   [How to: Create an Index Buffer](./overviews-direct3d-11-resources-buffers-index-how-to-69afb19bf1.md)
-   [How to: Create a Constant Buffer](./overviews-direct3d-11-resources-buffers-constant-how-to-cc243a75d3.md)
-   [How to: Initialize a Texture From a File](./overviews-direct3d-11-resources-textures-how-to-bdbf6f26ac.md)

## Multithreading Considerations

The amount of concurrency of resource creation and rendering that your application can achieve depends on the level of multithreading support that the driver implements. If the driver supports concurrent creates, then the application should have much less concurrency concerns. However, if the driver does not support concurrent object creation, the amount of concurrency is extremely limited. To understand the amount of support available in a driver, query the driver for the value of the **DriverConcurrentCreates** member of the [**D3D11\_FEATURE\_DATA\_THREADING**](./ns-d3d11-d3d11_feature_data_threading-a158baa93c.md) structure. For more information about checking for driver support of multithreading, see [How To: Check for Driver Support](./overviews-direct3d-11-render-multi-thread-support-ba2ebbde09.md).

Concurrent operations do not necessarily lead to better performance. For example, creating and loading a texture is typically limited by memory bandwidth. Attempting to create and load multiple textures might be no faster than doing one texture at a time, even if this leaves multiple CPU cores idle. However, creating multiple shaders using multiple threads can increase performance as this operation is less dependent on system resources such as memory bandwidth.

When the driver and graphics hardware support multithreading, you can typically initialize newly created resources more efficiently by passing a pointer to initial data in the *pInitialData* parameter (for example, in a call to the [**ID3D11Device::CreateTexture2D**](./nf-d3d11-id3d11device-createtexture2d-39a4608b7c.md) method).

## Related topics

<dl> <dt>

[MultiThreading](./overviews-direct3d-11-render-multi-thread-5aa955fbcb.md)
</dt> </dl>