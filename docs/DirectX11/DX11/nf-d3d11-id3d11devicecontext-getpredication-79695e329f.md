Source: [https://learn.microsoft.com/en-us/windows/win32/api/D3D11/nf-d3d11-id3d11devicecontext-getpredication](<https://learn.microsoft.com/en-us/windows/win32/api/D3D11/nf-d3d11-id3d11devicecontext-getpredication>)

# ID3D11DeviceContext::GetPredication


## -description

Get the rendering predicate state.

## -parameters

### -param ppPredicate [out, optional]

Type: <b><a href="/windows/desktop/api/d3d11/nn-d3d11-id3d11predicate">ID3D11Predicate</a>**</b>

Address of a pointer to a predicate (see <a href="/windows/desktop/api/d3d11/nn-d3d11-id3d11predicate">ID3D11Predicate</a>). Value stored here will be <b>NULL</b> upon device creation.

### -param pPredicateValue [out, optional]

Type: <b><a href="/windows/desktop/WinProg/windows-data-types">BOOL</a>*</b>

Address of a boolean to fill with the predicate comparison value. <b>FALSE</b> upon device creation.

## -remarks

Any returned interfaces will have their reference count incremented by one. Applications should call IUnknown::Release on the returned interfaces when they are no longer needed to avoid memory leaks.

## -see-also

<a href="/windows/desktop/api/d3d11/nn-d3d11-id3d11devicecontext">ID3D11DeviceContext</a>