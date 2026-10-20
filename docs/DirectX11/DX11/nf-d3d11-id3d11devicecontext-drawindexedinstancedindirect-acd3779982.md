Source: [https://learn.microsoft.com/en-us/windows/win32/api/D3D11/nf-d3d11-id3d11devicecontext-drawindexedinstancedindirect](<https://learn.microsoft.com/en-us/windows/win32/api/D3D11/nf-d3d11-id3d11devicecontext-drawindexedinstancedindirect>)

## -description

Draw indexed, instanced, GPU-generated primitives.

## -parameters

### -param pBufferForArgs [in]

Type: **[ID3D11Buffer](./nn-d3d11-id3d11buffer-0e4ba9908b.md)\***

A pointer to an [ID3D11Buffer](./nn-d3d11-id3d11buffer-0e4ba9908b.md), which is a buffer containing the GPU-generated primitives.

### -param AlignedByteOffsetForArgs [in]

Type: **[UINT](/windows/win32/winprog/windows-data-types)**

A DWORD-aligned byte offset in <i>pBufferForArgs</i> to the start of the GPU generated primitives.

## -remarks

When an application creates a buffer that is associated with the [ID3D11Buffer](./nn-d3d11-id3d11buffer-0e4ba9908b.md) interface that *pBufferForArgs* points to, your application must set the [D3D11_RESOURCE_MISC_DRAWINDIRECT_ARGS](./ne-d3d11-d3d11_resource_misc_flag-f85f09a16f.md) flag in the *MiscFlags* member of the [D3D11_BUFFER_DESC](./ns-d3d11-d3d11_buffer_desc-dbbb31b85c.md) structure that describes the buffer. To create the buffer, your application should call the [ID3D11Device::CreateBuffer](./nf-d3d11-id3d11device-createbuffer-973d575f5e.md) method, and pass a pointer to a **D3D11_BUFFER_DESC** in the *pDesc* parameter.

**Windows Phone 8:** This API is supported.

## -see-also

[ID3D11DeviceContext](./nn-d3d11-id3d11devicecontext-abe911f651.md)