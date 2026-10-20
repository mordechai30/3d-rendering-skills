Source: [https://learn.microsoft.com/en-us/windows/win32/api/D3D11/nf-d3d11-id3d11devicecontext-unmap](<https://learn.microsoft.com/en-us/windows/win32/api/D3D11/nf-d3d11-id3d11devicecontext-unmap>)

# ID3D11DeviceContext::Unmap


## -description

Invalidate the pointer to a resource and reenable the GPU's access to that resource.

## -parameters

### -param pResource [in]

Type: <b><a href="/windows/desktop/api/d3d11/nn-d3d11-id3d11resource">ID3D11Resource</a>*</b>

A pointer to a <a href="/windows/desktop/api/d3d11/nn-d3d11-id3d11resource">ID3D11Resource</a> interface.

### -param Subresource [in]

Type: <b><a href="/windows/desktop/WinProg/windows-data-types">UINT</a></b>

A subresource to be unmapped.

## -remarks

For info about how to use <b>Unmap</b>, see <a href="/windows/desktop/direct3d11/how-to--use-dynamic-resources">How to: Use dynamic resources</a>.
      

<b>Windows Phone 8:
        </b> This API is supported.

## -see-also

<a href="/windows/desktop/api/d3d11/nn-d3d11-id3d11devicecontext">ID3D11DeviceContext</a>