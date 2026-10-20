Source: [https://learn.microsoft.com/en-us/windows/win32/api/D3D11/nf-d3d11-id3d11devicecontext-omgetdepthstencilstate](<https://learn.microsoft.com/en-us/windows/win32/api/D3D11/nf-d3d11-id3d11devicecontext-omgetdepthstencilstate>)

# ID3D11DeviceContext::OMGetDepthStencilState


## -description

Gets the depth-stencil state of the output-merger stage.

## -parameters

### -param ppDepthStencilState [out, optional]

Type: <b><a href="/windows/desktop/api/d3d11/nn-d3d11-id3d11depthstencilstate">ID3D11DepthStencilState</a>**</b>

Address of a pointer to a depth-stencil state interface (see <a href="/windows/desktop/api/d3d11/nn-d3d11-id3d11depthstencilstate">ID3D11DepthStencilState</a>) to be filled with information from the device.

### -param pStencilRef [out, optional]

Type: <b><a href="/windows/desktop/WinProg/windows-data-types">UINT</a>*</b>

Pointer to the stencil reference value used in the depth-stencil test.

## -remarks

Any returned interfaces will have their reference count incremented by one. Applications should call IUnknown::Release on the returned interfaces when they are no longer needed to avoid memory leaks.

<b>Windows Phone 8:
        </b> This API is supported.

## -see-also

<a href="/windows/desktop/api/d3d11/nn-d3d11-id3d11devicecontext">ID3D11DeviceContext</a>