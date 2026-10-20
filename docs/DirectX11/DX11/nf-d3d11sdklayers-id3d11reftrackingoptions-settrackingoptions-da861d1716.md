Source: [https://learn.microsoft.com/en-us/windows/win32/api/D3D11SDKLayers/nf-d3d11sdklayers-id3d11reftrackingoptions-settrackingoptions](<https://learn.microsoft.com/en-us/windows/win32/api/D3D11SDKLayers/nf-d3d11sdklayers-id3d11reftrackingoptions-settrackingoptions>)

# ID3D11RefTrackingOptions::SetTrackingOptions


## -description

Sets graphics processing unit (GPU) debug reference tracking options.

## -parameters

### -param uOptions

A combination of <a href="/windows/win32/api/d3d11sdklayers/ne-d3d11sdklayers-d3d11_shader_tracking_options">D3D11_SHADER_TRACKING_OPTIONS</a>-typed flags that are combined by using a bitwise <b>OR</b> operation. The resulting value identifies tracking options. If a flag is present, the tracking option that the flag represents is set to "on"; otherwise the tracking option is set to "off."

## -returns

This method returns one of the <a href="/windows/desktop/direct3d11/d3d11-graphics-reference-returnvalues">Direct3D 11 return codes</a>.

## -remarks

This API requires the Windows Software Development Kit (SDK) for Windows 8.

## -see-also

<a href="/windows/desktop/api/d3d11sdklayers/nn-d3d11sdklayers-id3d11reftrackingoptions">ID3D11RefTrackingOptions</a>