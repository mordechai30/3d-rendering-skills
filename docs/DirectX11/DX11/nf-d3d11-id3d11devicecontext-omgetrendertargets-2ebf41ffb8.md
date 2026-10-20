Source: [https://learn.microsoft.com/en-us/windows/win32/api/D3D11/nf-d3d11-id3d11devicecontext-omgetrendertargets](<https://learn.microsoft.com/en-us/windows/win32/api/D3D11/nf-d3d11-id3d11devicecontext-omgetrendertargets>)

# ID3D11DeviceContext::OMGetRenderTargets


## -description

Get pointers to the resources bound to the output-merger stage.

## -parameters

### -param NumViews [in]

Type: <b><a href="/windows/desktop/WinProg/windows-data-types">UINT</a></b>

Number of render targets to retrieve.

### -param ppRenderTargetViews [out, optional]

Type: <b><a href="/windows/desktop/api/d3d11/nn-d3d11-id3d11rendertargetview">ID3D11RenderTargetView</a>**</b>

Pointer to an array of <a href="/windows/desktop/api/d3d11/nn-d3d11-id3d11rendertargetview">ID3D11RenderTargetView</a>s which represent render target views. Specify <b>NULL</b> for this parameter when retrieval of a render target is not needed.

### -param ppDepthStencilView [out, optional]

Type: <b><a href="/windows/desktop/api/d3d11/nn-d3d11-id3d11depthstencilview">ID3D11DepthStencilView</a>**</b>

Pointer to a <a href="/windows/desktop/api/d3d11/nn-d3d11-id3d11depthstencilview">ID3D11DepthStencilView</a>, which represents a depth-stencil view. Specify <b>NULL</b> for this parameter when retrieval of the depth-stencil view is not needed.

## -remarks

Any returned interfaces will have their reference count incremented by one. Applications should call IUnknown::Release on the returned interfaces when they are no longer needed to avoid memory leaks.

## -see-also

<a href="/windows/desktop/api/d3d11/nn-d3d11-id3d11devicecontext">ID3D11DeviceContext</a>