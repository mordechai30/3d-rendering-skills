Source: [https://learn.microsoft.com/en-us/windows/win32/api/D3D11_3/nf-d3d11_3-id3d11device3-createrasterizerstate2](<https://learn.microsoft.com/en-us/windows/win32/api/D3D11_3/nf-d3d11_3-id3d11device3-createrasterizerstate2>)

# ID3D11Device3::CreateRasterizerState2


## -description

Creates a rasterizer state object that informs the <a href="/windows/desktop/direct3d11/d3d10-graphics-programming-guide-rasterizer-stage">rasterizer stage</a> how to behave and forces the sample count while UAV rendering or rasterizing.

## -parameters

### -param pRasterizerDesc [in]

Type: <b>const <a href="/windows/desktop/api/d3d11_3/ns-d3d11_3-cd3d11_rasterizer_desc2">D3D11_RASTERIZER_DESC2</a>*</b>

A pointer to a <a href="/windows/desktop/api/d3d11_3/ns-d3d11_3-cd3d11_rasterizer_desc2">D3D11_RASTERIZER_DESC2</a> structure that describes the  rasterizer state.

### -param ppRasterizerState [out, optional]

Type: <b><a href="/windows/desktop/api/d3d11_3/nn-d3d11_3-id3d11rasterizerstate2">ID3D11RasterizerState2</a>**</b>

A pointer to a memory block that receives a pointer to a <a href="/windows/desktop/api/d3d11_3/nn-d3d11_3-id3d11rasterizerstate2">ID3D11RasterizerState2</a> interface for the created rasterizer state object. Set this parameter to <b>NULL</b> to validate the other input parameters (the method will return <b>S_FALSE</b> if the other input parameters pass validation).

## -returns

Type: <b><a href="/windows/win32/com/structure-of-com-error-codes">HRESULT</a></b>

This method returns E_OUTOFMEMORY if there is insufficient memory to create the rasterizer state object.  See <a href="/windows/desktop/direct3d11/d3d11-graphics-reference-returnvalues">Direct3D 11 Return Codes</a> for other possible return values.

## -see-also

<a href="/windows/desktop/api/d3d11_3/nn-d3d11_3-id3d11device3">ID3D11Device3</a>