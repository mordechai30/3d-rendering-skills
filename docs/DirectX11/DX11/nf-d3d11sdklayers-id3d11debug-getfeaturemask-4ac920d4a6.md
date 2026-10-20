Source: [https://learn.microsoft.com/en-us/windows/win32/api/D3D11SDKLayers/nf-d3d11sdklayers-id3d11debug-getfeaturemask](<https://learn.microsoft.com/en-us/windows/win32/api/D3D11SDKLayers/nf-d3d11sdklayers-id3d11debug-getfeaturemask>)

# ID3D11Debug::GetFeatureMask


## -description

Get a bitfield of flags that indicates which debug features are on or off.



## -returns

Type: <b><a href="/windows/desktop/WinProg/windows-data-types">UINT</a></b>

Mask of feature-mask flags bitwise ORed together. If a flag is present, then that feature will be set to on, otherwise the feature will be set to off. See <a href="/windows/desktop/api/d3d11sdklayers/nf-d3d11sdklayers-id3d11debug-setfeaturemask">ID3D11Debug::SetFeatureMask</a> for a list of possible feature-mask flags.

## -see-also

<a href="/windows/desktop/api/d3d11sdklayers/nn-d3d11sdklayers-id3d11debug">ID3D11Debug Interface</a>