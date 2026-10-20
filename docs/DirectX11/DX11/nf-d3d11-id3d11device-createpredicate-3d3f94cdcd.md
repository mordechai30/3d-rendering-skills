Source: [https://learn.microsoft.com/en-us/windows/win32/api/D3D11/nf-d3d11-id3d11device-createpredicate](<https://learn.microsoft.com/en-us/windows/win32/api/D3D11/nf-d3d11-id3d11device-createpredicate>)

# ID3D11Device::CreatePredicate


## -description

Creates a predicate.

## -parameters

### -param pPredicateDesc [in]

Type: <b>const <a href="/windows/desktop/api/d3d11/ns-d3d11-d3d11_query_desc">D3D11_QUERY_DESC</a>*</b>

Pointer to a query description where the type of query must be a D3D11_QUERY_SO_OVERFLOW_PREDICATE or D3D11_QUERY_OCCLUSION_PREDICATE (see <a href="/windows/desktop/api/d3d11/ns-d3d11-d3d11_query_desc">D3D11_QUERY_DESC</a>).

### -param ppPredicate [out, optional]

Type: <b><a href="/windows/desktop/api/d3d11/nn-d3d11-id3d11predicate">ID3D11Predicate</a>**</b>

Address of a pointer to a predicate (see <a href="/windows/desktop/api/d3d11/nn-d3d11-id3d11predicate">ID3D11Predicate</a>).

## -returns

Type: <b><a href="/windows/win32/com/structure-of-com-error-codes">HRESULT</a></b>

This method returns one of the following <a href="/windows/desktop/direct3d11/d3d11-graphics-reference-returnvalues">Direct3D 11 Return Codes</a>.

## -see-also

<a href="/windows/desktop/api/d3d11/nn-d3d11-id3d11device">ID3D11Device</a>