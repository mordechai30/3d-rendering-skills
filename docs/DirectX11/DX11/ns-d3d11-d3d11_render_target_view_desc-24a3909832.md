Source: [https://learn.microsoft.com/en-us/windows/win32/api/D3D11/ns-d3d11-d3d11_render_target_view_desc](<https://learn.microsoft.com/en-us/windows/win32/api/D3D11/ns-d3d11-d3d11_render_target_view_desc>)

# D3D11_RENDER_TARGET_VIEW_DESC structure


## -description

Specifies the subresources from a resource that are accessible using a render-target view.

## -struct-fields

### -field Format

Type: <b><a href="/windows/desktop/api/dxgiformat/ne-dxgiformat-dxgi_format">DXGI_FORMAT</a></b>

The data format (see <a href="/windows/desktop/api/dxgiformat/ne-dxgiformat-dxgi_format">DXGI_FORMAT</a>).

### -field ViewDimension

Type: <b><a href="/windows/desktop/api/d3d11/ne-d3d11-d3d11_rtv_dimension">D3D11_RTV_DIMENSION</a></b>

The resource type (see <a href="/windows/desktop/api/d3d11/ne-d3d11-d3d11_rtv_dimension">D3D11_RTV_DIMENSION</a>), which specifies how the render-target resource will be accessed.

### -field Buffer

Type: <b><a href="/windows/desktop/api/d3d11/ns-d3d11-d3d11_buffer_rtv">D3D11_BUFFER_RTV</a></b>

Specifies which buffer elements can be accessed (see <a href="/windows/desktop/api/d3d11/ns-d3d11-d3d11_buffer_rtv">D3D11_BUFFER_RTV</a>).

### -field Texture1D

Type: <b><a href="/windows/desktop/api/d3d11/ns-d3d11-d3d11_tex1d_rtv">D3D11_TEX1D_RTV</a></b>

Specifies the subresources in a 1D texture that can be accessed (see <a href="/windows/desktop/api/d3d11/ns-d3d11-d3d11_tex1d_rtv">D3D11_TEX1D_RTV</a>).

### -field Texture1DArray

Type: <b><a href="/windows/desktop/api/d3d11/ns-d3d11-d3d11_tex1d_array_rtv">D3D11_TEX1D_ARRAY_RTV</a></b>

Specifies the subresources in a 1D texture array that can be accessed (see <a href="/windows/desktop/api/d3d11/ns-d3d11-d3d11_tex1d_array_rtv">D3D11_TEX1D_ARRAY_RTV</a>).

### -field Texture2D

Type: <b><a href="/windows/desktop/api/d3d11/ns-d3d11-d3d11_tex2d_rtv">D3D11_TEX2D_RTV</a></b>

Specifies the subresources in a 2D texture that can be accessed (see <a href="/windows/desktop/api/d3d11/ns-d3d11-d3d11_tex2d_rtv">D3D11_TEX2D_RTV</a>).

### -field Texture2DArray

Type: <b><a href="/windows/desktop/api/d3d11/ns-d3d11-d3d11_tex2d_array_rtv">D3D11_TEX2D_ARRAY_RTV</a></b>

Specifies the subresources in a 2D texture array that can be accessed (see <a href="/windows/desktop/api/d3d11/ns-d3d11-d3d11_tex2d_array_rtv">D3D11_TEX2D_ARRAY_RTV</a>).

### -field Texture2DMS

Type: <b><a href="/windows/desktop/api/d3d11/ns-d3d11-d3d11_tex2dms_rtv">D3D11_TEX2DMS_RTV</a></b>

Specifies a single subresource because a multisampled 2D texture only contains one subresource (see <a href="/windows/desktop/api/d3d11/ns-d3d11-d3d11_tex2dms_rtv">D3D11_TEX2DMS_RTV</a>).

### -field Texture2DMSArray

Type: <b><a href="/windows/desktop/api/d3d11/ns-d3d11-d3d11_tex2dms_array_rtv">D3D11_TEX2DMS_ARRAY_RTV</a></b>

Specifies the subresources in a multisampled 2D texture array that can be accessed (see <a href="/windows/desktop/api/d3d11/ns-d3d11-d3d11_tex2dms_array_rtv">D3D11_TEX2DMS_ARRAY_RTV</a>).

### -field Texture3D

Type: <b><a href="/windows/desktop/api/d3d11/ns-d3d11-d3d11_tex3d_rtv">D3D11_TEX3D_RTV</a></b>

Specifies subresources in a 3D texture that can be accessed (see <a href="/windows/desktop/api/d3d11/ns-d3d11-d3d11_tex3d_rtv">D3D11_TEX3D_RTV</a>).

## -remarks

A render-target-view description is passed into <a href="/windows/desktop/api/d3d11/nf-d3d11-id3d11device-createrendertargetview">ID3D11Device::CreateRenderTargetView</a> to create a render target.

A render-target-view cannot use the following formats:

<ul>
<li>Any typeless format.</li>
<li>DXGI_FORMAT_R32G32B32 if the view will be used to bind a buffer (vertex, index, constant, or stream-output).</li>
</ul>
If the format is set to DXGI_FORMAT_UNKNOWN, then the format of the resource that the view binds to the pipeline will be used.

## -see-also

<a href="/windows/desktop/direct3d11/d3d11-graphics-reference-resource-structures">Resource Structures</a>