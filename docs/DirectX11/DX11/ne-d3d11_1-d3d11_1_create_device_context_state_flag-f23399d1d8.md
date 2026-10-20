Source: [https://learn.microsoft.com/en-us/windows/win32/api/D3D11_1/ne-d3d11_1-d3d11_1_create_device_context_state_flag](<https://learn.microsoft.com/en-us/windows/win32/api/D3D11_1/ne-d3d11_1-d3d11_1_create_device_context_state_flag>)

# D3D11_1_CREATE_DEVICE_CONTEXT_STATE_FLAG enumeration


## -description

Describes flags that are used to create a device context state object (<a href="/windows/desktop/api/d3d11_1/nn-d3d11_1-id3ddevicecontextstate">ID3DDeviceContextState</a>) with the <a href="/windows/desktop/api/d3d11_1/nf-d3d11_1-id3d11device1-createdevicecontextstate">ID3D11Device1::CreateDeviceContextState</a> method.

## -enum-fields

### -field D3D11_1_CREATE_DEVICE_CONTEXT_STATE_SINGLETHREADED:0x1

You use this flag if your application will only call methods of Direct3D 11 and Direct3D 10 interfaces from a single thread. By default, Direct3D 11 and Direct3D 10 are  <a href="/windows/desktop/direct3d11/overviews-direct3d-11-render-multi-thread-differences">thread-safe</a>. 
        By using this flag, you can increase performance. However, if you use this flag and your application calls methods from multiple threads, undefined behavior might result.

## -see-also

<a href="/windows/desktop/direct3d11/d3d11-graphics-reference-d3d11-core-enums">Core Enumerations</a>



<a href="/windows/desktop/api/d3d11_1/nf-d3d11_1-id3d11device1-createdevicecontextstate">ID3D11Device1::CreateDeviceContextState</a>