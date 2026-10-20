Source: [https://learn.microsoft.com/en-us/windows/win32/api/D3D11_1/nf-d3d11_1-id3d11devicecontext1-discardresource](<https://learn.microsoft.com/en-us/windows/win32/api/D3D11_1/nf-d3d11_1-id3d11devicecontext1-discardresource>)

# ID3D11DeviceContext1::DiscardResource


## -description

Discards a resource from the device context.

## -parameters

### -param pResource [in]

Type: <b><a href="/windows/desktop/api/d3d11/nn-d3d11-id3d11resource">ID3D11Resource</a>*</b>

A pointer to the <a href="/windows/desktop/api/d3d11/nn-d3d11-id3d11resource">ID3D11Resource</a> interface for the resource to discard. The resource must have been created with usage <a href="/windows/desktop/api/d3d11/ne-d3d11-d3d11_usage">D3D11_USAGE_DEFAULT</a> or <a href="/windows/desktop/api/d3d11/ne-d3d11-d3d11_usage">D3D11_USAGE_DYNAMIC</a>, otherwise the runtime drops the call to <b>DiscardResource</b>; if the debug layer is enabled, the runtime returns an error message.

## -remarks

<b>DiscardResource</b> informs the graphics processing unit (GPU) that the existing content in the resource that <i>pResource</i> points to is no longer needed.

## -see-also

<a href="/windows/desktop/api/d3d11_1/nn-d3d11_1-id3d11devicecontext1">ID3D11DeviceContext1</a>