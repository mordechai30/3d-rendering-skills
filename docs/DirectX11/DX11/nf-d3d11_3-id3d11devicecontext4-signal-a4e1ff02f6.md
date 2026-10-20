Source: [https://learn.microsoft.com/en-us/windows/win32/api/d3d11_3/nf-d3d11_3-id3d11devicecontext4-signal](<https://learn.microsoft.com/en-us/windows/win32/api/d3d11_3/nf-d3d11_3-id3d11devicecontext4-signal>)

# ID3D11DeviceContext4::Signal


## -description

Updates a fence to a specified value after all previous work has completed.

This member function is equivalent to the Direct3D 12 <a href="/windows/win32/api/d3d12/nf-d3d12-id3d12commandqueue-signal">ID3D12CommandQueue::Signal</a> member function, and applies between Direct3D 11 and Direct3D 12 in interop scenarios.
<div class="alert"><b>Note</b>  This method only applies to immediate-mode contexts.</div><div> </div>

## -parameters

### -param pFence

Type: <b><a href="/windows/win32/api/d3d11_3/nn-d3d11_3-id3d11fence">ID3D11Fence</a>*</b>

A pointer to the <a href="/windows/win32/api/d3d11_3/nn-d3d11_3-id3d11fence">ID3D11Fence</a> object.

### -param Value

Type: <b><a href="/windows/win32/WinProg/windows-data-types">UINT64</a></b>

The value to set the fence to.

## -returns

Type: <b><a href="/windows/win32/com/structure-of-com-error-codes">HRESULT</a></b>

This method returns one of the <a href="/windows/win32/direct3d11/d3d11-graphics-reference-returnvalues">Direct3D 11 Return Codes</a>.

## -see-also

<a href="/windows/win32/api/d3d11_3/nn-d3d11_3-id3d11devicecontext4">ID3D11DeviceContext4</a>



<a href="/windows/win32/direct3d12/user-mode-heap-synchronization">Multi-engine synchronization</a>