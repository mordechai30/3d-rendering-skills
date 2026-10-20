Source: [https://learn.microsoft.com/en-us/windows/win32/direct3d11/overviews-direct3d-11-render-multi-thread-render](<https://learn.microsoft.com/en-us/windows/win32/direct3d11/overviews-direct3d-11-render-multi-thread-render>)

# Immediate and Deferred Rendering

Direct3D 11 supports two types of rendering: immediate and deferred. Both are implemented by using the [**ID3D11DeviceContext**](./nn-d3d11-id3d11devicecontext-abe911f651.md) interface.

## Immediate Rendering

Immediate rendering refers to calling rendering APIs or commands from a device, which queues the commands in a buffer for execution on the GPU. Use an immediate context to render, set pipeline state, and play back a command list.

Create an immediate context using [**D3D11CreateDevice**](./nf-d3d11-d3d11createdevice-fbcd3f07e1.md) or [**D3D11CreateDeviceAndSwapChain**](./nf-d3d11-d3d11createdeviceandswapchain-5744e33d11.md).

## Deferred Rendering

Deferred rendering records graphics commands in a command buffer so that they can be played back at some other time. Use a deferred context to record commands (rendering as well as state setting) to a command list. Deferred rendering is a new concept in Direct3D 11; deferred rendering is designed to support rendering on one thread while recording commands for rendering on additional threads. This parallel, multithread strategy allows you to break up complex scenes into concurrent tasks. For more information about rendering complex scenes, see [Multiple-Pass Rendering](./overviews-direct3d-11-render-multipass-98ff50cd25.md).

Create a deferred context using [**ID3D11Device::CreateDeferredContext**](./nf-d3d11-id3d11device-createdeferredcontext-2d9c0ea4a7.md).

Direct3D generates rendering overhead when it queues up commands in the command buffer. In contrast, a [command list](./overviews-direct3d-11-render-multi-thread-command-list-e1b0cabde9.md) executes much more efficiently during playback. To use a command list, record rendering commands with a deferred context and play them back using an immediate context.

You can generate only a single command list in a single-threaded fashion. However, you can create and use multiple deferred contexts simultaneously, each in a separate thread. Then, you can use those multiple deferred contexts to simultaneously create multiple command lists.

You cannot play back two or more command lists simultaneously on the immediate context.

To determine if a device context is an immediate or a deferred context, call [**ID3D11DeviceContext::GetType**](./nf-d3d11-id3d11devicecontext-gettype-5f5484ec2a.md).

The [**ID3D11DeviceContext::Map**](./nf-d3d11-id3d11devicecontext-map-d6df2a4196.md) method is only supported in a deferred context for dynamic resources ([**D3D11\_USAGE\_DYNAMIC**](./ne-d3d11-d3d11_usage-8197affe09.md)) where the first call within the command list is [**D3D11\_MAP\_WRITE\_DISCARD**](./ne-d3d11-d3d11_map-80dcff5b4f.md). **D3D11\_MAP\_WRITE\_NO\_OVERWRITE** is supported on subsequent calls if available for the given type of resource.

Queries in a deferred context are limited to data generation and predicated drawing. You cannot call [**ID3D11DeviceContext::GetData**](./nf-d3d11-id3d11devicecontext-getdata-3fb2bae12b.md) on a deferred context to get data about a query; you can only call **GetData** on the immediate context to get data about a query. You can set a rendering predicate (a type of query) by calling [**D3D11DeviceContext::SetPredication**](./nf-d3d11-id3d11devicecontext-setpredication-431da802c7.md) to use query results on the GPU. You can generate query data through calls to [**ID3D11DeviceContext::Begin**](./nf-d3d11-id3d11devicecontext-begin-c9556fba9e.md) and [**ID3D11DeviceContext::End**](./nf-d3d11-id3d11devicecontext-end-410cf19035.md). However, the query data will not be available until you call [**ID3D11DeviceContext::ExecuteCommandList**](./nf-d3d11-id3d11devicecontext-executecommandlist-9a13a31f2f.md) on the immediate context to submit the deferred context command list. The query data is then processed by the GPU.

## Related topics

<dl> <dt>

[Multithreading](./overviews-direct3d-11-render-multi-thread-5aa955fbcb.md)
</dt> </dl>