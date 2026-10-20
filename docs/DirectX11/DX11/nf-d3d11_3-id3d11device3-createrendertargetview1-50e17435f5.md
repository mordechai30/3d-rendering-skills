Source: [https://learn.microsoft.com/en-us/windows/win32/api/D3D11_3/nf-d3d11_3-id3d11device3-createrendertargetview1](<https://learn.microsoft.com/en-us/windows/win32/api/D3D11_3/nf-d3d11_3-id3d11device3-createrendertargetview1>)

# ID3D11Device3::CreateRenderTargetView1


## -description

Creates a render-target view for accessing resource data.

## -parameters

### -param pResource [in]

Type: <b><a href="/windows/desktop/api/d3d11/nn-d3d11-id3d11resource">ID3D11Resource</a>*</b>

Pointer to a <a href="/windows/desktop/api/d3d11/nn-d3d11-id3d11resource">ID3D11Resource</a> that represents a render target. This resource must have been created with the <a href="/windows/desktop/api/d3d11/ne-d3d11-d3d11_bind_flag">D3D11_BIND_RENDER_TARGET</a> flag.

### -param pDesc1 [in, optional]

Type: <b>const <a href="/windows/win32/api/d3d11_3/ns-d3d11_3-d3d11_render_target_view_desc1">D3D11_RENDER_TARGET_VIEW_DESC1</a>*</b>

Pointer to a <a href="/windows/win32/api/d3d11_3/ns-d3d11_3-d3d11_render_target_view_desc1">D3D11_RENDER_TARGET_VIEW_DESC1</a> that represents a render-target view description. Set this parameter to <b>NULL</b> to create a view that accesses all of the subresources in mipmap level 0.

### -param ppRTView1 [out, optional]

Type: <b><a href="/windows/desktop/api/d3d11_3/nn-d3d11_3-id3d11rendertargetview1">ID3D11RenderTargetView1</a>**</b>

A pointer to a memory block that receives a pointer to a <a href="/windows/desktop/api/d3d11_3/nn-d3d11_3-id3d11rendertargetview1">ID3D11RenderTargetView1</a> interface for the created render-target view. Set this parameter to <b>NULL</b> to validate the other input parameters (the method will return <b>S_FALSE</b> if the other input parameters pass validation).

## -returns

Type: <b><a href="/windows/win32/com/structure-of-com-error-codes">HRESULT</a></b>

This method returns one of the <a href="/windows/desktop/direct3d11/d3d11-graphics-reference-returnvalues">Direct3D 11 Return Codes</a>.

## -remarks

A render-target view can be bound to the output-merger stage by calling <a href="/windows/desktop/api/d3d11/nf-d3d11-id3d11devicecontext-omsetrendertargets">ID3D11DeviceContext::OMSetRenderTargets</a>.

## -see-also

<a href="/windows/desktop/api/d3d11_3/nn-d3d11_3-id3d11device3">ID3D11Device3</a>