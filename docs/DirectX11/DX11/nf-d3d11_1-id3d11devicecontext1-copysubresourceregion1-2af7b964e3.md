Source: [https://learn.microsoft.com/en-us/windows/win32/api/D3D11_1/nf-d3d11_1-id3d11devicecontext1-copysubresourceregion1](<https://learn.microsoft.com/en-us/windows/win32/api/D3D11_1/nf-d3d11_1-id3d11devicecontext1-copysubresourceregion1>)

# ID3D11DeviceContext1::CopySubresourceRegion1


## -description

Copies a region from a source resource to a destination resource.

## -parameters

### -param pDstResource [in]

Type: <b><a href="/windows/desktop/api/d3d11/nn-d3d11-id3d11resource">ID3D11Resource</a>*</b>

A pointer to the destination resource.

### -param DstSubresource [in]

Type: <b><a href="/windows/desktop/WinProg/windows-data-types">UINT</a></b>

Destination subresource index.

### -param DstX [in]

Type: <b><a href="/windows/desktop/WinProg/windows-data-types">UINT</a></b>

The x-coordinate of the upper-left corner of the destination region.

### -param DstY [in]

Type: <b><a href="/windows/desktop/WinProg/windows-data-types">UINT</a></b>

The y-coordinate of the upper-left corner of the destination region. For a 1D subresource, this must be zero.

### -param DstZ [in]

Type: <b><a href="/windows/desktop/WinProg/windows-data-types">UINT</a></b>

The z-coordinate of the upper-left corner of the destination region. For a 1D or 2D subresource, this must be zero.

### -param pSrcResource [in]

Type: <b><a href="/windows/desktop/api/d3d11/nn-d3d11-id3d11resource">ID3D11Resource</a>*</b>

A pointer to the source resource.

### -param SrcSubresource [in]

Type: <b><a href="/windows/desktop/WinProg/windows-data-types">UINT</a></b>

Source subresource index.

### -param pSrcBox [in, optional]

Type: <b>const <a href="/windows/desktop/api/d3d11/ns-d3d11-d3d11_box">D3D11_BOX</a>*</b>

A pointer to a 3D box that defines the region of the source subresource that <b>CopySubresourceRegion1</b> can copy. If <b>NULL</b>, <b>CopySubresourceRegion1</b> copies the entire source subresource. The box must fit within the source resource.

An empty box results in a no-op. A box is empty if the top value is greater than or equal to the bottom value, or the left value is greater than or equal to the right value, or the front value is greater than or equal to the back value. When the box is empty, <b>CopySubresourceRegion1</b> doesn't perform a copy operation.

### -param CopyFlags [in]

Type: <b><a href="/windows/desktop/WinProg/windows-data-types">UINT</a></b>

A <a href="/windows/desktop/api/d3d11_1/ne-d3d11_1-d3d11_copy_flags">D3D11_COPY_FLAGS</a>-typed value that specifies how to perform the copy operation. If you specify zero for no copy option, <b>CopySubresourceRegion1</b> behaves like <a href="/windows/desktop/api/d3d11/nf-d3d11-id3d11devicecontext-copysubresourceregion">ID3D11DeviceContext::CopySubresourceRegion</a>. For existing display drivers that can't process these flags, the runtime doesn't use them.

## -remarks

If the display driver supports overlapping, the source and destination subresources can be identical, and the source and destination regions can overlap each other.  For existing display drivers that don’t support overlapping, the runtime drops calls with identical source and destination subresources, regardless of whether the regions overlap.  To determine whether the display driver supports overlapping, check the <b>CopyWithOverlap</b> member of <a href="/windows/desktop/api/d3d11/ns-d3d11-d3d11_feature_data_d3d11_options">D3D11_FEATURE_DATA_D3D11_OPTIONS</a>. This overlapping support enables additional scroll functionality in a call to <a href="/windows/desktop/api/dxgi/nf-dxgi-idxgiswapchain-present">IDXGISwapChain::Present</a>.

<div class="alert"><b>Note</b>  <b>Applies only to feature level 9_x hardware</b> If you use <a href="/windows/desktop/api/d3d11_1/nf-d3d11_1-id3d11devicecontext1-updatesubresource1">ID3D11DeviceContext1::UpdateSubresource1</a> or <b>CopySubresourceRegion1</b> to copy from a staging resource to a default resource, you can corrupt the destination contents. This occurs if you pass a <b>NULL</b> source box and if the source resource has different dimensions from those of the destination resource or if you use destination offsets, (x, y, and z). In this situation, always pass a source box that is the full size of the source resource.</div>
<div> </div>

## -see-also

<a href="/windows/desktop/api/d3d11_1/nn-d3d11_1-id3d11devicecontext1">ID3D11DeviceContext1</a>