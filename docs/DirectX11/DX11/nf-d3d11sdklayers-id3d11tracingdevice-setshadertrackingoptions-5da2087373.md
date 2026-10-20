Source: [https://learn.microsoft.com/en-us/windows/win32/api/D3D11SDKLayers/nf-d3d11sdklayers-id3d11tracingdevice-setshadertrackingoptions](<https://learn.microsoft.com/en-us/windows/win32/api/D3D11SDKLayers/nf-d3d11sdklayers-id3d11tracingdevice-setshadertrackingoptions>)

# ID3D11TracingDevice::SetShaderTrackingOptions


## -description

Sets the reference rasterizer's race-condition tracking options for a specific shader.

## -parameters

### -param pShader [in]

A pointer to the <a href="/windows/desktop/api/unknwn/nn-unknwn-iunknown">IUnknown</a> interface of a shader.

### -param Options [in]

A combination of <a href="/windows/win32/api/d3d11sdklayers/ne-d3d11sdklayers-d3d11_shader_tracking_options">D3D11_SHADER_TRACKING_OPTIONS</a>-typed flags that are combined by using a bitwise <b>OR</b> operation. The resulting value identifies tracking options. If a flag is present, the tracking option that the flag represents is set to "on"; otherwise the tracking option is set to "off."

## -returns

This method returns one of the <a href="/windows/desktop/direct3d11/d3d11-graphics-reference-returnvalues">Direct3D 11 return codes</a>.

## -remarks

[D3D11_SHADER_TRACKING_OPTION_UAV_SPECIFIC_FLAGS](./ne-d3d11sdklayers-d3d11_shader_tracking_options-94357982f8.md)) in the <i>Options</i> parameter for a compute shader, <b>SetShaderTrackingOptions</b> ignores it.</div>
<div> </div>
<div class="alert"><b>Note</b>  This API requires the Windows Software Development Kit (SDK) for Windows 8.</div>
<div> </div>

## -see-also

<a href="/windows/desktop/api/d3d11sdklayers/nn-d3d11sdklayers-id3d11tracingdevice">ID3D11TracingDevice</a>