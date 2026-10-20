Source: [https://learn.microsoft.com/en-us/windows/win32/api/D3D11SDKLayers/nf-d3d11sdklayers-id3d11debug-getswapchain](<https://learn.microsoft.com/en-us/windows/win32/api/D3D11SDKLayers/nf-d3d11sdklayers-id3d11debug-getswapchain>)

# ID3D11Debug::GetSwapChain


## -description

Get the swap chain that the runtime will use for automatically calling <a href="/windows/desktop/api/dxgi/nf-dxgi-idxgiswapchain-present">IDXGISwapChain::Present</a>.

## -parameters

### -param ppSwapChain [out]

Type: <b><a href="/windows/desktop/api/dxgi/nn-dxgi-idxgiswapchain">IDXGISwapChain</a>**</b>

Swap chain that the runtime will use for automatically calling <a href="/windows/desktop/api/dxgi/nf-dxgi-idxgiswapchain-present">IDXGISwapChain::Present</a>.

## -returns

Type: <b><a href="/windows/win32/com/structure-of-com-error-codes">HRESULT</a></b>

This method returns one of the following <a href="/windows/desktop/direct3d11/d3d11-graphics-reference-returnvalues">Direct3D 11 Return Codes</a>.

## -remarks

The swap chain retrieved by this method will only be used if D3D11_DEBUG_FEATURE_PRESENT_PER_RENDER_OP is set in the <a href="/windows/desktop/api/d3d11sdklayers/nf-d3d11sdklayers-id3d11debug-setfeaturemask">feature mask</a>.

## -see-also

<a href="/windows/desktop/api/d3d11sdklayers/nn-d3d11sdklayers-id3d11debug">ID3D11Debug Interface</a>