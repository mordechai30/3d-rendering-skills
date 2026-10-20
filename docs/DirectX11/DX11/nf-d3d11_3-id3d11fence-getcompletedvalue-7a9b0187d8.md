Source: [https://learn.microsoft.com/en-us/windows/win32/api/D3D11_3/nf-d3d11_3-id3d11fence-getcompletedvalue](<https://learn.microsoft.com/en-us/windows/win32/api/D3D11_3/nf-d3d11_3-id3d11fence-getcompletedvalue>)

# ID3D11Fence::GetCompletedValue


## -description

Gets the current value of the fence.

This member function is equivalent to the Direct3D 12 <a href="/windows/win32/api/d3d12/nf-d3d12-id3d12fence-getcompletedvalue">ID3D12Fence::GetCompletedValue</a> member function, and applies between Direct3D 11 and Direct3D 12 in interop scenarios.



## -returns

Type: <b><a href="/windows/win32/WinProg/windows-data-types">UINT64</a></b>

Returns the current value of the fence.

## -see-also

<a href="/windows/win32/api/d3d11_3/nn-d3d11_3-id3d11fence">ID3D11Fence</a>



<a href="/windows/win32/direct3d12/user-mode-heap-synchronization">Multi-engine synchronization</a>