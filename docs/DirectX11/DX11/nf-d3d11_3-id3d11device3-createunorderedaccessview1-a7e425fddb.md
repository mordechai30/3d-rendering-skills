Source: [https://learn.microsoft.com/en-us/windows/win32/api/D3D11_3/nf-d3d11_3-id3d11device3-createunorderedaccessview1](<https://learn.microsoft.com/en-us/windows/win32/api/D3D11_3/nf-d3d11_3-id3d11device3-createunorderedaccessview1>)

# ID3D11Device3::CreateUnorderedAccessView1


## -description

Creates a view for accessing an <a href="/windows/desktop/direct3d11/direct3d-11-advanced-stages-cs-resources">unordered access</a> resource.

## -parameters

### -param pResource [in]

Type: <b><a href="/windows/desktop/api/d3d11/nn-d3d11-id3d11resource">ID3D11Resource</a>*</b>

Pointer to an <a href="/windows/desktop/api/d3d11/nn-d3d11-id3d11resource">ID3D11Resource</a> that represents a resources that will serve as an input to a shader.

### -param pDesc1 [in, optional]

Type: <b>const <a href="/windows/desktop/api/d3d11_3/ns-d3d11_3-cd3d11_unordered_access_view_desc1">D3D11_UNORDERED_ACCESS_VIEW_DESC1</a>*</b>

Pointer to a <a href="/windows/desktop/api/d3d11_3/ns-d3d11_3-cd3d11_unordered_access_view_desc1">D3D11_UNORDERED_ACCESS_VIEW_DESC1</a> structure that represents an unordered-access view description. Set this parameter to <b>NULL</b> to create a view that accesses the entire resource (using the format the resource was created with).

### -param ppUAView1 [out, optional]

Type: <b><a href="/windows/desktop/api/d3d11_3/nn-d3d11_3-id3d11unorderedaccessview1">ID3D11UnorderedAccessView1</a>**</b>

A pointer to a memory block that receives a pointer to a <a href="/windows/desktop/api/d3d11_3/nn-d3d11_3-id3d11unorderedaccessview1">ID3D11UnorderedAccessView1</a> interface for the created unordered-access view. Set this parameter to <b>NULL</b> to validate the other input parameters (the method will return <b>S_FALSE</b> if the other input parameters pass validation).

## -returns

Type: <b><a href="/windows/win32/com/structure-of-com-error-codes">HRESULT</a></b>

This method returns E_OUTOFMEMORY if there is insufficient memory to create the unordered-access view.  See <a href="/windows/desktop/direct3d11/d3d11-graphics-reference-returnvalues">Direct3D 11 Return Codes</a> for other possible return values.

## -see-also

<a href="/windows/desktop/api/d3d11_3/nn-d3d11_3-id3d11device3">ID3D11Device3</a>