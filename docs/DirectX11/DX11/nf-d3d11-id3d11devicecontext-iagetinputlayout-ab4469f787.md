Source: [https://learn.microsoft.com/en-us/windows/win32/api/D3D11/nf-d3d11-id3d11devicecontext-iagetinputlayout](<https://learn.microsoft.com/en-us/windows/win32/api/D3D11/nf-d3d11-id3d11devicecontext-iagetinputlayout>)

# ID3D11DeviceContext::IAGetInputLayout


## -description

Get a pointer to the input-layout object that is bound to the input-assembler stage.

## -parameters

### -param ppInputLayout [out]

Type: <b><a href="/windows/desktop/api/d3d11/nn-d3d11-id3d11inputlayout">ID3D11InputLayout</a>**</b>

A pointer to the input-layout object (see <a href="/windows/desktop/api/d3d11/nn-d3d11-id3d11inputlayout">ID3D11InputLayout</a>), which describes the input buffers that will be read by the IA stage.

## -remarks

For information about creating an input-layout object, see Creating the Input-Layout Object.

Any returned interfaces will have their reference count incremented by one. Applications should call IUnknown::Release on the returned interfaces when they are no longer needed to avoid memory leaks.

## -see-also

<a href="/windows/desktop/api/d3d11/nn-d3d11-id3d11devicecontext">ID3D11DeviceContext</a>