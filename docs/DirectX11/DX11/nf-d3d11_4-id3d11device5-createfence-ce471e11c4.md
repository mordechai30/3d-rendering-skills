Source: [https://learn.microsoft.com/en-us/windows/win32/api/d3d11_4/nf-d3d11_4-id3d11device5-createfence](<https://learn.microsoft.com/en-us/windows/win32/api/d3d11_4/nf-d3d11_4-id3d11device5-createfence>)

# ID3D11Device5::CreateFence


## -description

Creates a fence object.

This member function is equivalent to the Direct3D 12 <a href="/windows/desktop/api/d3d12/nf-d3d12-id3d12device-createfence">ID3D12Device::CreateFence</a> member function, and applies between Direct3D 11 and Direct3D 12 in interop scenarios.

## -parameters

### -param InitialValue

Type: <b><a href="/windows/desktop/WinProg/windows-data-types">UINT64</a></b>

The initial value for the fence.

### -param Flags

Type: <b><a href="/windows/desktop/api/d3d11_3/ne-d3d11_3-d3d11_fence_flag">D3D11_FENCE_FLAG</a></b>

A combination of <a href="/windows/desktop/api/d3d11_3/ne-d3d11_3-d3d11_fence_flag">D3D11_FENCE_FLAG</a>-typed values that are combined by using a bitwise OR operation. 
            The resulting value specifies options for the fence.

### -param ReturnedInterface

Type: <b>REFIID</b>

The globally unique identifier (<b>GUID</b>) for the fence interface (<a href="/windows/desktop/api/d3d11_3/nn-d3d11_3-id3d11fence">ID3D11Fence</a>).
            The <b>REFIID</b>, or <b>GUID</b>, of the interface to the fence can be obtained by using the __uuidof() macro.
            For example, __uuidof(ID3D11Fence) will get the <b>GUID</b> of the interface to a fence.

### -param ppFence [out]

Type: <b>void**</b>

A pointer to a memory block that receives a pointer to the <a href="/windows/desktop/api/d3d11_3/nn-d3d11_3-id3d11fence">ID3D11Fence</a> interface that is used to access the fence.

## -returns

Type: <b><a href="/windows/desktop/WinProg/windows-data-types">HRESULT</a></b>

Returns <b>S_OK</b> if successful; otherwise, returns one of the <a href="/windows/desktop/direct3d11/d3d11-graphics-reference-returnvalues">Direct3D 11 Return Codes</a>.

## -see-also

<a href="/windows/desktop/api/d3d11_4/nn-d3d11_4-id3d11device5">ID3D11Device5</a>



<a href="/windows/desktop/api/d3d11_4/nf-d3d11_4-id3d11device4-unregisterdeviceremoved">UnregisterDeviceRemoved</a>