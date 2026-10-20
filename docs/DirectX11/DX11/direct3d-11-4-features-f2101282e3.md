Source: [https://learn.microsoft.com/en-us/windows/win32/direct3d11/direct3d-11-4-features](<https://learn.microsoft.com/en-us/windows/win32/direct3d11/direct3d-11-4-features>)

# Direct3D 11.4 Features

The following functionality has been added in Direct3D 11.4.

Also see [Where is the DirectX SDK?](../directx-sdk--august-2009-.md).

## Direct3D device removal

The [**RegisterDeviceRemovedEvent**](./nf-d3d11_4-id3d11device4-registerdeviceremovedevent-4c8f79c923.md), and [**UnregisterDeviceRemoved**](./nf-d3d11_4-id3d11device4-unregisterdeviceremoved-54b837375e.md) methods are supported by a new interface, [**ID3D11Device4**](./nn-d3d11_4-id3d11device4-45b2ad76bb.md), to support receiving an asynchronous event notification when a Direct3D device has been removed.

## Multithreaded protection

To ensure that graphics commands in particular are executed in a specific order, the [**ID3D11Multithread**](./nn-d3d11_4-id3d11multithread-2deb2a7bcc.md) interface has methods to turn multithread protection on and off, and methods to enter and leave critical code requiring this protection.

## Fences for multi-device synchronization and interop with Direct3D 12

The [**ID3D11Fence**](./nn-d3d11_3-id3d11fence-d61cfd96ca.md), [**ID3D11Device5**](./nn-d3d11_4-id3d11device5-79a18ccbff.md) and [**ID3D11DeviceContext4**](./nn-d3d11_3-id3d11devicecontext4-fcc3c83a40.md) provide the same fence functionality as Direct3D 12 for Direct3D 11. Fences are used to synchronize multiple Direct3D11 devices, and for interop between Direct3D 11 and Direct3D 12. Fences are supported in the Windows 10 Creators Update.

## Extended NV12 texture support

NV12 textures with capture and video encode capabilities now support sharing. Older D3D11 texture flags for video encode and capture are deprecated for NV12, as it will be set all the time for new drivers. Such textures can be shared not only with D3D11, but also with D3D12. In D3D12, no new flags represent these texture capabilities.

Refer to the boolean setting in [**D3D11\_FEATURE\_DATA\_D3D11\_OPTIONS4**](./ns-d3d11_4-d3d11_feature_data_d3d11_options4-c5ec219f7b.md).

## Shader Caching

Drivers may support OS-managed shader caching of Direct3D11 applications in the Windows 10 Creators update.

## Related topics

<dl> <dt>

[What's new in Direct3D 11](./dx-graphics-overviews-introduction-99897347f0.md)
</dt> </dl>