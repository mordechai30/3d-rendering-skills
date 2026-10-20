Source: [https://learn.microsoft.com/en-us/windows/win32/api/D3D11SDKLayers/nf-d3d11sdklayers-id3d11debug-getpresentperrenderopdelay](<https://learn.microsoft.com/en-us/windows/win32/api/D3D11SDKLayers/nf-d3d11sdklayers-id3d11debug-getpresentperrenderopdelay>)

# ID3D11Debug::GetPresentPerRenderOpDelay


## -description

Get the number of milliseconds to sleep after <a href="/windows/desktop/api/dxgi/nf-dxgi-idxgiswapchain-present">IDXGISwapChain::Present</a> is called.



## -returns

Type: <b><a href="/windows/desktop/WinProg/windows-data-types">UINT</a></b>

Number of milliseconds to sleep after Present is called.

## -remarks

Value is set with <a href="/windows/desktop/api/d3d11sdklayers/nf-d3d11sdklayers-id3d11debug-setpresentperrenderopdelay">ID3D11Debug::SetPresentPerRenderOpDelay</a>.

## -see-also

<a href="/windows/desktop/api/d3d11sdklayers/nn-d3d11sdklayers-id3d11debug">ID3D11Debug Interface</a>