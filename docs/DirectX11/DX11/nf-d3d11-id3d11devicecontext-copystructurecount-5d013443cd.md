Source: [https://learn.microsoft.com/en-us/windows/win32/api/D3D11/nf-d3d11-id3d11devicecontext-copystructurecount](<https://learn.microsoft.com/en-us/windows/win32/api/D3D11/nf-d3d11-id3d11devicecontext-copystructurecount>)

# ID3D11DeviceContext::CopyStructureCount


## -description

Copies data from a buffer holding variable length data.

## -parameters

### -param pDstBuffer [in]

Type: <b><a href="/windows/desktop/api/d3d11/nn-d3d11-id3d11buffer">ID3D11Buffer</a>*</b>

Pointer to <a href="/windows/desktop/api/d3d11/nn-d3d11-id3d11buffer">ID3D11Buffer</a>.  This can be any buffer resource that other copy commands, 
        such as <a href="/windows/desktop/api/d3d11/nf-d3d11-id3d11devicecontext-copyresource">ID3D11DeviceContext::CopyResource</a> or <a href="/windows/desktop/api/d3d11/nf-d3d11-id3d11devicecontext-copysubresourceregion">ID3D11DeviceContext::CopySubresourceRegion</a>, are able to write to.

### -param DstAlignedByteOffset [in]

Type: <b><a href="/windows/desktop/WinProg/windows-data-types">UINT</a></b>

Offset from the start of <i>pDstBuffer</i> to write 32-bit UINT structure (vertex) count from <i>pSrcView</i>.

### -param pSrcView [in]

Type: <b><a href="/windows/desktop/api/d3d11/nn-d3d11-id3d11unorderedaccessview">ID3D11UnorderedAccessView</a>*</b>

Pointer to an <a href="/windows/desktop/api/d3d11/nn-d3d11-id3d11unorderedaccessview">ID3D11UnorderedAccessView</a> of a Structured Buffer resource created with either 
        <a href="/windows/desktop/api/d3d11/ne-d3d11-d3d11_buffer_uav_flag">D3D11_BUFFER_UAV_FLAG_APPEND</a> or <b>D3D11_BUFFER_UAV_FLAG_COUNTER</b> specified 
        when the UAV was created.   These types of resources have hidden counters tracking "how many" records have 
        been written.

## -see-also

<a href="/windows/desktop/api/d3d11/nn-d3d11-id3d11devicecontext">ID3D11DeviceContext</a>