Source: [https://learn.microsoft.com/en-us/windows/win32/api/D3D11_3/nf-d3d11_3-id3d11device3-createquery1](<https://learn.microsoft.com/en-us/windows/win32/api/D3D11_3/nf-d3d11_3-id3d11device3-createquery1>)

# ID3D11Device3::CreateQuery1


## -description

Creates a query object for querying information from the graphics processing unit (GPU).

## -parameters

### -param pQueryDesc1 [in]

Type: <b>const <a href="/windows/desktop/api/d3d11_3/ns-d3d11_3-cd3d11_query_desc1">D3D11_QUERY_DESC1</a>*</b>

Pointer to a <a href="/windows/desktop/api/d3d11_3/ns-d3d11_3-cd3d11_query_desc1">D3D11_QUERY_DESC1</a> structure that represents a query description.

### -param ppQuery1 [out, optional]

Type: <b><a href="/windows/desktop/api/d3d11_3/nn-d3d11_3-id3d11query1">ID3D11Query1</a>**</b>

A pointer to a memory block that receives a pointer to a <a href="/windows/desktop/api/d3d11_3/nn-d3d11_3-id3d11query1">ID3D11Query1</a> interface for the created query object. Set this parameter to <b>NULL</b> to validate the other input parameters (the method will return <b>S_FALSE</b> if the other input parameters pass validation).

## -returns

Type: <b><a href="/windows/win32/com/structure-of-com-error-codes">HRESULT</a></b>

This method returns E_OUTOFMEMORY if there is insufficient memory to create the query object.  
        See <a href="/windows/desktop/direct3d11/d3d11-graphics-reference-returnvalues">Direct3D 11 Return Codes</a> for other possible return values.

## -see-also

<a href="/windows/desktop/api/d3d11_3/nn-d3d11_3-id3d11device3">ID3D11Device3</a>