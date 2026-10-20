Source: [https://learn.microsoft.com/en-us/windows/win32/api/d3d11_4/nf-d3d11_4-id3d11device5-opensharedfence](<https://learn.microsoft.com/en-us/windows/win32/api/d3d11_4/nf-d3d11_4-id3d11device5-opensharedfence>)

# ID3D11Device5::OpenSharedFence


## -description

Opens a handle for a shared fence by using HANDLE and REFIID.

This member function is a limited version of the Direct3D 12 <a href="/windows/win32/api/d3d12/nf-d3d12-id3d12device-opensharedhandle">ID3D12Device::OpenSharedHandle</a> member function, and applies between Direct3D 11 and Direct3D 12 in interop scenarios. Unlike <b>ID3D12Device::OpenSharedHandle</b> which operates on resources, heaps, and fences, the <b>ID3D11Device5::OpenSharedFence</b> function only operates on fences; in Direct3D 11, shared resources are opened with the [ID3D11Device::OpenSharedResource1](./nf-d3d11_1-id3d11device1-opensharedresource1-623a94192a.md) member function.

## -parameters

### -param hFence [in]

Type: <b>HANDLE</b>

The handle that was returned by a call to <a href="/windows/win32/api/d3d11_3/nf-d3d11_3-id3d11fence-createsharedhandle">ID3D11Fence::CreateSharedHandle</a> or <a href="/windows/win32/api/d3d12/nf-d3d12-id3d12device-createsharedhandle">ID3D12Device::CreateSharedHandle</a>.

### -param ReturnedInterface

Type: <b>REFIID</b>

The globally unique identifier (<b>GUID</b>) for the <a href="/windows/win32/api/d3d11_3/nn-d3d11_3-id3d11fence">ID3D11Fence</a> interface. The <b>REFIID</b>, or <b>GUID</b>, of the interface can be obtained by using the __uuidof() macro. For example, __uuidof(ID3D11Fence) will get the <b>GUID</b> of the interface to the fence.

### -param ppFence [out, optional]

Type: <b>void**</b>

A pointer to a memory block that receives a pointer to the <a href="/windows/win32/api/d3d11_3/nn-d3d11_3-id3d11fence">ID3D11Fence</a> interface.

## -returns

Type: <b><a href="/windows/win32/com/structure-of-com-error-codes">HRESULT</a></b>

This method returns one of the <a href="/windows/win32/direct3d11/d3d11-graphics-reference-returnvalues">Direct3D 11 Return Codes</a>.

## -see-also

[ID3D11Device5](./nn-d3d11_4-id3d11device5-79a18ccbff.md), [Multi-adapter systems](/windows/win32/direct3d12/multi-engine)