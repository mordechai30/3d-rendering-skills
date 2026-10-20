Source: [https://learn.microsoft.com/en-us/windows/win32/api/D3D11/nf-d3d11-id3d11device-createrasterizerstate](<https://learn.microsoft.com/en-us/windows/win32/api/D3D11/nf-d3d11-id3d11device-createrasterizerstate>)

# ID3D11Device::CreateRasterizerState


## -description

Create a rasterizer state object that tells the rasterizer stage how to behave.

## -parameters

### -param pRasterizerDesc [in]

Type: <b>const <a href="/windows/desktop/api/d3d11/ns-d3d11-d3d11_rasterizer_desc">D3D11_RASTERIZER_DESC</a>*</b>

Pointer to a rasterizer state description (see <a href="/windows/desktop/api/d3d11/ns-d3d11-d3d11_rasterizer_desc">D3D11_RASTERIZER_DESC</a>).

### -param ppRasterizerState [out, optional]

Type: <b><a href="/windows/desktop/api/d3d11/nn-d3d11-id3d11rasterizerstate">ID3D11RasterizerState</a>**</b>

Address of a pointer to the rasterizer state object created (see <a href="/windows/desktop/api/d3d11/nn-d3d11-id3d11rasterizerstate">ID3D11RasterizerState</a>).

## -returns

Type: <b><a href="/windows/win32/com/structure-of-com-error-codes">HRESULT</a></b>

This method returns E_OUTOFMEMORY if there is insufficient memory to create the compute shader.  See <a href="/windows/desktop/direct3d11/d3d11-graphics-reference-returnvalues">Direct3D 11 Return Codes</a> for other possible return values.

## -remarks

4096 unique rasterizer state objects can be created on a device at a time.

If an application attempts to create a rasterizer-state interface with the same state as an existing interface, the same interface will be returned and the total number of unique rasterizer state objects will stay the same.

## -see-also

<a href="/windows/desktop/api/d3d11/nn-d3d11-id3d11device">ID3D11Device</a>