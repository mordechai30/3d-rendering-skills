Source: [https://learn.microsoft.com/en-us/windows/win32/api/D3D11SDKLayers/nf-d3d11sdklayers-id3d11debug-setswapchain](<https://learn.microsoft.com/en-us/windows/win32/api/D3D11SDKLayers/nf-d3d11sdklayers-id3d11debug-setswapchain>)

# ID3D11Debug::SetSwapChain


## -description

Sets a swap chain that the runtime will use for automatically calling <a href="/windows/desktop/api/dxgi/nf-dxgi-idxgiswapchain-present">IDXGISwapChain::Present</a>.

## -parameters

### -param pSwapChain [in, optional]

Type: <b><a href="/windows/desktop/api/dxgi/nn-dxgi-idxgiswapchain">IDXGISwapChain</a>*</b>

Swap chain that the runtime will use for automatically calling <a href="/windows/desktop/api/dxgi/nf-dxgi-idxgiswapchain-present">IDXGISwapChain::Present</a>; must have been created with the DXGI_SWAP_EFFECT_SEQUENTIAL swap-effect flag.

## -returns

Type: <b><a href="/windows/win32/com/structure-of-com-error-codes">HRESULT</a></b>

This method returns one of the following <a href="/windows/desktop/direct3d11/d3d11-graphics-reference-returnvalues">Direct3D 11 Return Codes</a>.

## -remarks

<div class="alert"><b>Note</b>  If you call this API in a Session 0 process, it returns <a href="/windows/desktop/direct3ddxgi/dxgi-error">DXGI_ERROR_NOT_CURRENTLY_AVAILABLE</a>.</div>
<div> </div>
The swap chain set by this method will only be used if D3D11_DEBUG_FEATURE_PRESENT_PER_RENDER_OP is set in the <a href="/windows/desktop/api/d3d11sdklayers/nf-d3d11sdklayers-id3d11debug-setfeaturemask">feature mask</a>.

## -see-also

<a href="/windows/desktop/api/d3d11sdklayers/nn-d3d11sdklayers-id3d11debug">ID3D11Debug Interface</a>