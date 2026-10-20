Source: [https://learn.microsoft.com/en-us/windows/win32/api/D3D11SDKLayers/nf-d3d11sdklayers-id3d11debug-reportlivedeviceobjects](<https://learn.microsoft.com/en-us/windows/win32/api/D3D11SDKLayers/nf-d3d11sdklayers-id3d11debug-reportlivedeviceobjects>)

# ID3D11Debug::ReportLiveDeviceObjects


## -description

Report information about a device object's lifetime.

## -parameters

### -param Flags

Type: <b><a href="/windows/desktop/api/d3d11sdklayers/ne-d3d11sdklayers-d3d11_rldo_flags">D3D11_RLDO_FLAGS</a></b>

A value from the
            <a href="/windows/desktop/api/d3d11sdklayers/ne-d3d11sdklayers-d3d11_rldo_flags">D3D11_RLDO_FLAGS</a> enumeration.

## -returns

Type: <b><a href="/windows/win32/com/structure-of-com-error-codes">HRESULT</a></b>

This method returns one of the following <a href="/windows/desktop/direct3d11/d3d11-graphics-reference-returnvalues">Direct3D 11 Return Codes</a>.

## -remarks

<b>ReportLiveDeviceObjects</b> uses the value in  <i>Flags</i> to determine the amount of information to report about a device object's lifetime.

## -see-also

<a href="/windows/desktop/api/d3d11sdklayers/nn-d3d11sdklayers-id3d11debug">ID3D11Debug Interface</a>