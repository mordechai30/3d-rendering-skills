Source: [https://learn.microsoft.com/en-us/windows/win32/api/D3D11/nf-d3d11-id3d11device-createrendertargetview](<https://learn.microsoft.com/en-us/windows/win32/api/D3D11/nf-d3d11-id3d11device-createrendertargetview>)

# ID3D11Device::CreateRenderTargetView


## -description

Creates a render-target view for accessing resource data.

## -parameters

### -param pResource [in]

Type: <b><a href="/windows/desktop/api/d3d11/nn-d3d11-id3d11resource">ID3D11Resource</a>*</b>

Pointer to a <a href="/windows/desktop/api/d3d11/nn-d3d11-id3d11resource">ID3D11Resource</a> that represents a render target. This resource must have been created with the <a href="/windows/desktop/api/d3d11/ne-d3d11-d3d11_bind_flag">D3D11_BIND_RENDER_TARGET</a> flag.

### -param pDesc [in, optional]

Type: <b>const <a href="/windows/desktop/api/d3d11/ns-d3d11-d3d11_render_target_view_desc">D3D11_RENDER_TARGET_VIEW_DESC</a>*</b>

Pointer to a <a href="/windows/desktop/api/d3d11/ns-d3d11-d3d11_render_target_view_desc">D3D11_RENDER_TARGET_VIEW_DESC</a> that represents a render-target view description. Set this parameter to <b>NULL</b> to create a view that accesses all of the subresources in mipmap level 0.

### -param ppRTView [out, optional]

Type: <b><a href="/windows/desktop/api/d3d11/nn-d3d11-id3d11rendertargetview">ID3D11RenderTargetView</a>**</b>

Address of a pointer to an <a href="/windows/desktop/api/d3d11/nn-d3d11-id3d11rendertargetview">ID3D11RenderTargetView</a>. Set this parameter to <b>NULL</b> to validate the other input parameters (the method will return S_FALSE if the other input parameters pass validation).

## -returns

Type: <b><a href="/windows/win32/com/structure-of-com-error-codes">HRESULT</a></b>

This method returns one of the <a href="/windows/desktop/direct3d11/d3d11-graphics-reference-returnvalues">Direct3D 11 Return Codes</a>.

## -remarks

A render-target view can be bound to the output-merger stage by calling <a href="/windows/desktop/api/d3d11/nf-d3d11-id3d11devicecontext-omsetrendertargets">ID3D11DeviceContext::OMSetRenderTargets</a>.

The Direct3D 11.1 runtime, which is available starting with Windows 8, allows you to use <b>CreateRenderTargetView</b> for the following new purpose. 

You can create render-target views of video resources so that Direct3D shaders can process those render-target views. These video resources are either <a href="/windows/desktop/direct3dhlsl/sm5-object-texture2d">Texture2D</a> or <a href="/windows/desktop/direct3dhlsl/sm5-object-texture2darray">Texture2DArray</a>. The value in the <b>ViewDimension</b> member of the <a href="/windows/desktop/api/d3d11/ns-d3d11-d3d11_render_target_view_desc">D3D11_RENDER_TARGET_VIEW_DESC</a> structure for a created render-target view must match the type of video resource, D3D11_RTV_DIMENSION_TEXTURE2D          for Texture2D and D3D11_RTV_DIMENSION_TEXTURE2DARRAY for Texture2DArray. Additionally, the format of the underlying video resource restricts the formats that the view can use. The video resource format values on the <a href="/windows/desktop/api/dxgiformat/ne-dxgiformat-dxgi_format">DXGI_FORMAT</a> reference page specify the format values that views are restricted to.

The runtime read+write conflict prevention logic (which stops a resource from being bound as an SRV and RTV or UAV at the same time) treats views of different parts of the same video surface as conflicting for simplicity.  Therefore, the runtime does not allow an application to read from luma while the application simultaneously renders to chroma in the same surface even though the hardware might allow these simultaneous operations.

## -see-also

<a href="/windows/desktop/api/d3d11/nn-d3d11-id3d11device">ID3D11Device</a>