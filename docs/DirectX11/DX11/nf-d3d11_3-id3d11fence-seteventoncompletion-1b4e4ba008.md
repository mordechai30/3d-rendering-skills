Source: [https://learn.microsoft.com/en-us/windows/win32/api/D3D11_3/nf-d3d11_3-id3d11fence-seteventoncompletion](<https://learn.microsoft.com/en-us/windows/win32/api/D3D11_3/nf-d3d11_3-id3d11fence-seteventoncompletion>)

# ID3D11Fence::SetEventOnCompletion


## -description

Specifies an event that should be fired when the fence reaches a certain value.

This member function is equivalent to the Direct3D 12 <a href="/windows/win32/api/d3d12/nf-d3d12-id3d12fence-seteventoncompletion">ID3D12Fence::SetEventOnCompletion</a> member function, and applies between Direct3D 11 and Direct3D 12 in interop scenarios.

## -parameters

### -param Value

Type: <b><a href="/windows/win32/WinProg/windows-data-types">UINT64</a></b>

The fence value when the event is to be signaled.

### -param hEvent

Type: <b><a href="/windows/win32/WinProg/windows-data-types">HANDLE</a></b>

A handle to the event object.

## -returns

Type: <b>HRESULT</b>

This method returns <b>E_OUTOFMEMORY</b> if the kernel components don’t have sufficient memory to store the event in a list. See <a href="/windows/win32/direct3d11/d3d11-graphics-reference-returnvalues">Direct3D 11 Return Codes</a> for other possible return values.

## -see-also

<a href="/windows/win32/api/d3d11_3/nn-d3d11_3-id3d11fence">ID3D11Fence</a>



<a href="/windows/win32/direct3d12/user-mode-heap-synchronization">Multi-engine synchronization</a>