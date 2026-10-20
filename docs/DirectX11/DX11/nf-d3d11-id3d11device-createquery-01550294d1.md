Source: [https://learn.microsoft.com/en-us/windows/win32/api/D3D11/nf-d3d11-id3d11device-createquery](<https://learn.microsoft.com/en-us/windows/win32/api/D3D11/nf-d3d11-id3d11device-createquery>)

# ID3D11Device::CreateQuery


## -description

This interface encapsulates methods for querying information from the GPU.

## -parameters

### -param pQueryDesc [in]

Type: <b>const <a href="/windows/desktop/api/d3d11/ns-d3d11-d3d11_query_desc">D3D11_QUERY_DESC</a>*</b>

Pointer to a query description (see <a href="/windows/desktop/api/d3d11/ns-d3d11-d3d11_query_desc">D3D11_QUERY_DESC</a>).

### -param ppQuery [out, optional]

Type: <b><a href="/windows/desktop/api/d3d11/nn-d3d11-id3d11query">ID3D11Query</a>**</b>

Address of a pointer to the query object created (see <a href="/windows/desktop/api/d3d11/nn-d3d11-id3d11query">ID3D11Query</a>).

## -returns

Type: <b><a href="/windows/win32/com/structure-of-com-error-codes">HRESULT</a></b>

This method returns E_OUTOFMEMORY if there is insufficient memory to create the query object.  
        See <a href="/windows/desktop/direct3d11/d3d11-graphics-reference-returnvalues">Direct3D 11 Return Codes</a> for other possible return values.

## -see-also

<a href="/windows/desktop/api/d3d11/nn-d3d11-id3d11device">ID3D11Device</a>