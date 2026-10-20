Source: [https://learn.microsoft.com/en-us/windows/win32/api/D3D11_1/nf-d3d11_1-id3d11device1-createrasterizerstate1](<https://learn.microsoft.com/en-us/windows/win32/api/D3D11_1/nf-d3d11_1-id3d11device1-createrasterizerstate1>)

# ID3D11Device1::CreateRasterizerState1


## -description

Creates a rasterizer state object that informs the <a href="/windows/desktop/direct3d11/d3d10-graphics-programming-guide-rasterizer-stage">rasterizer stage</a> how to behave and forces the sample count while UAV rendering or rasterizing.

## -parameters

### -param pRasterizerDesc [in]

A pointer to a <a href="/windows/desktop/api/d3d11_1/ns-d3d11_1-cd3d11_rasterizer_desc1">D3D11_RASTERIZER_DESC1</a> structure that describes the  rasterizer state.

### -param ppRasterizerState [out, optional]

Address of a pointer to the <a href="/windows/desktop/api/d3d11_1/nn-d3d11_1-id3d11rasterizerstate1">ID3D11RasterizerState1</a> interface for the rasterizer state object created.

## -returns

This method returns E_OUTOFMEMORY if there is insufficient memory to create the rasterizer state object.  See <a href="/windows/desktop/direct3d11/d3d11-graphics-reference-returnvalues">Direct3D 11 Return Codes</a> for other possible return values.

## -remarks

An app can create up to 4096 unique rasterizer state objects. For each object created, the runtime checks to see if a previous object 
      has the same state. If such a previous object exists, the runtime will return a pointer to previous instance instead of creating a duplicate object.

## -see-also

<a href="/windows/desktop/api/d3d11_1/nn-d3d11_1-id3d11device1">ID3D11Device1</a>