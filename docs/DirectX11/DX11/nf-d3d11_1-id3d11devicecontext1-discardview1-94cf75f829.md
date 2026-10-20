Source: [https://learn.microsoft.com/en-us/windows/win32/api/D3D11_1/nf-d3d11_1-id3d11devicecontext1-discardview1](<https://learn.microsoft.com/en-us/windows/win32/api/D3D11_1/nf-d3d11_1-id3d11devicecontext1-discardview1>)

# ID3D11DeviceContext1::DiscardView1


## -description

Discards the specified elements in a resource view from the device context.

## -parameters

### -param pResourceView [in]

Type: <b><a href="/windows/desktop/api/d3d11/nn-d3d11-id3d11view">ID3D11View</a>*</b>

A pointer to the <a href="/windows/desktop/api/d3d11/nn-d3d11-id3d11view">ID3D11View</a> interface for the resource view to discard. The resource that underlies the view must have been created with usage <a href="/windows/desktop/api/d3d11/ne-d3d11-d3d11_usage">D3D11_USAGE_DEFAULT</a> or <a href="/windows/desktop/api/d3d11/ne-d3d11-d3d11_usage">D3D11_USAGE_DYNAMIC</a>, otherwise the runtime drops the call to <b>DiscardView1</b>; if the debug layer is enabled, the runtime returns an error message.

### -param pRects [in, optional]

Type: <b>const <a href="/windows/desktop/direct3d11/d3d11-rect">D3D11_RECT</a>*</b>

An array of <a href="/windows/desktop/direct3d11/d3d11-rect">D3D11_RECT</a> structures for the rectangles in the resource view to discard. If <b>NULL</b>, <b>DiscardView1</b> discards the entire view and behaves the same as <a href="/windows/desktop/api/d3d11_1/nf-d3d11_1-id3d11devicecontext1-discardview">DiscardView</a>.

### -param NumRects

Type: <b><a href="/windows/desktop/WinProg/windows-data-types">UINT</a></b>

Number of rectangles in the array that the  <i>pRects</i> parameter specifies.

## -remarks

<b>DiscardView1</b> informs the graphics processing unit (GPU) that the existing content in the specified elements in the resource view that <i>pResourceView</i> points to is no longer needed.  The view can be an SRV, RTV, UAV, or DSV.  <b>DiscardView1</b> is a variation on the <a href="/windows/desktop/api/d3d11_1/nf-d3d11_1-id3d11devicecontext1-discardresource">DiscardResource</a> method.  <b>DiscardView1</b> allows you to discard elements of a subset of a resource that is in a view (such as elements of a single miplevel).  More importantly, <b>DiscardView1</b> provides a convenience because often views are what are being bound and unbound at the pipeline.  Some pipeline bindings do not have views, such as stream output.  In that situation, <b>DiscardResource</b> can do the job for any resource.

## -see-also

<a href="/windows/desktop/api/d3d11_1/nn-d3d11_1-id3d11devicecontext1">ID3D11DeviceContext1</a>