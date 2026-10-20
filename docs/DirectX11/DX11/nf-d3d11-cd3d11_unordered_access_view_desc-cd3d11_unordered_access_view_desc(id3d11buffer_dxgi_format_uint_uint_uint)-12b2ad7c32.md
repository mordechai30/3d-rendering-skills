Source: [https://learn.microsoft.com/en-us/windows/win32/api/d3d11/nf-d3d11-cd3d11_unordered_access_view_desc-cd3d11_unordered_access_view_desc(id3d11buffer_dxgi_format_uint_uint_uint)](<https://learn.microsoft.com/en-us/windows/win32/api/d3d11/nf-d3d11-cd3d11_unordered_access_view_desc-cd3d11_unordered_access_view_desc(id3d11buffer_dxgi_format_uint_uint_uint)>)

# CD3D11_UNORDERED_ACCESS_VIEW_DESC::CD3D11_UNORDERED_ACCESS_VIEW_DESC(ID3D11Buffer,DXGI_FORMAT,UINT,UINT,UINT)


## -description

Instantiates a new instance of a <a href="/previous-versions/windows/desktop/legacy/jj151712(v=vs.85)">CD3D11_UNORDERED_ACCESS_VIEW_DESC</a> structure that is initialized with **D3D11_BUFFER_UAV** values.

## -parameters

### -param unnamedParam1

A pointer to a **ID3D11Buffer** interface for a buffer.

### -param format

A **DXGI_FORMAT**-typed value that specifies the viewing format.

### -param firstElement

Number of bytes between the beginning of the buffer and the first element to access.

### -param numElements

Total number of elements in the view.

### -param flags

A **D3D11_BUFFER_UAV_FLAG**-typed value that identifies view options for a buffer.

## -see-also

<a href="/previous-versions/windows/desktop/legacy/jj151712(v=vs.85)">CD3D11_UNORDERED_ACCESS_VIEW_DESC</a>