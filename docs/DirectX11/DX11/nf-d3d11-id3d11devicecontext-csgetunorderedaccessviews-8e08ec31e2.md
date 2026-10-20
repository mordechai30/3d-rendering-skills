Source: [https://learn.microsoft.com/en-us/windows/win32/api/D3D11/nf-d3d11-id3d11devicecontext-csgetunorderedaccessviews](<https://learn.microsoft.com/en-us/windows/win32/api/D3D11/nf-d3d11-id3d11devicecontext-csgetunorderedaccessviews>)

# ID3D11DeviceContext::CSGetUnorderedAccessViews


## -description

Gets an array of views for an unordered resource.

## -parameters

### -param StartSlot [in]

Type: <b><a href="/windows/desktop/WinProg/windows-data-types">UINT</a></b>

Index of the first element in the zero-based array to return (ranges from 0 to D3D11_1_UAV_SLOT_COUNT - 1).

### -param NumUAVs [in]

Type: <b><a href="/windows/desktop/WinProg/windows-data-types">UINT</a></b>

Number of views to get (ranges from 0 to D3D11_1_UAV_SLOT_COUNT - StartSlot).

### -param ppUnorderedAccessViews [out, optional]

Type: <b><a href="/windows/desktop/api/d3d11/nn-d3d11-id3d11unorderedaccessview">ID3D11UnorderedAccessView</a>**</b>

A pointer to an array of interface pointers (see <a href="/windows/desktop/api/d3d11/nn-d3d11-id3d11unorderedaccessview">ID3D11UnorderedAccessView</a>) to get.

## -remarks

Any returned interfaces will have their reference count incremented by one. Applications should call <b>IUnknown::Release</b> on the returned interfaces when they are no longer needed to avoid memory leaks.

## -see-also

<a href="/windows/desktop/api/d3d11/nn-d3d11-id3d11devicecontext">ID3D11DeviceContext</a>