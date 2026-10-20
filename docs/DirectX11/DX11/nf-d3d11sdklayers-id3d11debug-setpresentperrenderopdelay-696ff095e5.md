Source: [https://learn.microsoft.com/en-us/windows/win32/api/D3D11SDKLayers/nf-d3d11sdklayers-id3d11debug-setpresentperrenderopdelay](<https://learn.microsoft.com/en-us/windows/win32/api/D3D11SDKLayers/nf-d3d11sdklayers-id3d11debug-setpresentperrenderopdelay>)

# ID3D11Debug::SetPresentPerRenderOpDelay


## -description

Set the number of milliseconds to sleep after <a href="/windows/desktop/api/dxgi/nf-dxgi-idxgiswapchain-present">IDXGISwapChain::Present</a> is called.

## -parameters

### -param Milliseconds

Type: <b><a href="/windows/desktop/WinProg/windows-data-types">UINT</a></b>

Number of milliseconds to sleep after Present is called.

## -returns

Type: <b><a href="/windows/win32/com/structure-of-com-error-codes">HRESULT</a></b>

This method returns one of the following <a href="/windows/desktop/direct3d11/d3d11-graphics-reference-returnvalues">Direct3D 11 Return Codes</a>.

## -remarks

<div class="alert"><b>Note</b>  If you call this API in a Session 0 process, it returns <a href="/windows/desktop/direct3ddxgi/dxgi-error">DXGI_ERROR_NOT_CURRENTLY_AVAILABLE</a>.</div>
<div> </div>
The application will only sleep if D3D11_DEBUG_FEATURE_PRESENT_PER_RENDER_OP is a set in the <a href="/windows/desktop/api/d3d11sdklayers/nf-d3d11sdklayers-id3d11debug-setfeaturemask">feature mask</a>. If that flag is not set the number of milliseconds is set but ignored and the application does not sleep. 10ms is used as a default value if this method is never called.

## -see-also

<a href="/windows/desktop/api/d3d11sdklayers/nn-d3d11sdklayers-id3d11debug">ID3D11Debug Interface</a>