Source: [https://learn.microsoft.com/en-us/windows/win32/api/D3D11/nf-d3d11-id3d11devicecontext-omgetrendertargetsandunorderedaccessviews](<https://learn.microsoft.com/en-us/windows/win32/api/D3D11/nf-d3d11-id3d11devicecontext-omgetrendertargetsandunorderedaccessviews>)

# ID3D11DeviceContext::OMGetRenderTargetsAndUnorderedAccessViews


## -description

Get pointers to the resources bound to the output-merger stage.

## -parameters

### -param NumRTVs [in]

Type: <b><a href="/windows/desktop/WinProg/windows-data-types">UINT</a></b>

The number of render-target views to retrieve.

### -param ppRenderTargetViews [out, optional]

Type: <b><a href="/windows/desktop/api/d3d11/nn-d3d11-id3d11rendertargetview">ID3D11RenderTargetView</a>**</b>

Pointer to an array of <a href="/windows/desktop/api/d3d11/nn-d3d11-id3d11rendertargetview">ID3D11RenderTargetView</a>s, which represent render-target views. Specify <b>NULL</b> for this parameter when retrieval of render-target views is not required.

### -param ppDepthStencilView [out, optional]

Type: <b><a href="/windows/desktop/api/d3d11/nn-d3d11-id3d11depthstencilview">ID3D11DepthStencilView</a>**</b>

Pointer to a <a href="/windows/desktop/api/d3d11/nn-d3d11-id3d11depthstencilview">ID3D11DepthStencilView</a>, which represents a depth-stencil view. Specify <b>NULL</b> for this parameter when retrieval of the depth-stencil view is not required.

### -param UAVStartSlot [in]

Type: <b><a href="/windows/desktop/WinProg/windows-data-types">UINT</a></b>

Index into a zero-based array to begin retrieving unordered-access views (ranges from 0 to D3D11_PS_CS_UAV_REGISTER_COUNT - 1).
            For pixel shaders <i>UAVStartSlot</i> should be equal to the number of render-target views that are bound.

### -param NumUAVs [in]

Type: <b><a href="/windows/desktop/WinProg/windows-data-types">UINT</a></b>

Number of unordered-access views to return in <i>ppUnorderedAccessViews</i>. This number ranges from 0 to D3D11_PS_CS_UAV_REGISTER_COUNT - <i>UAVStartSlot</i>.

### -param ppUnorderedAccessViews [out, optional]

Type: <b><a href="/windows/desktop/api/d3d11/nn-d3d11-id3d11unorderedaccessview">ID3D11UnorderedAccessView</a>**</b>

Pointer to an array of <a href="/windows/desktop/api/d3d11/nn-d3d11-id3d11unorderedaccessview">ID3D11UnorderedAccessView</a>s, which represent unordered-access views that are retrieved. Specify <b>NULL</b> for this parameter when retrieval of unordered-access views is not required.

## -remarks

Any returned interfaces will have their reference count incremented by one. Applications should call <a href="/windows/desktop/api/unknwn/nf-unknwn-iunknown-release">IUnknown::Release</a> on the returned interfaces when they are no longer needed to avoid memory leaks.
        

<b>Windows Phone 8:
        </b> This API is supported.

## -see-also

<a href="/windows/desktop/api/d3d11/nn-d3d11-id3d11devicecontext">ID3D11DeviceContext</a>