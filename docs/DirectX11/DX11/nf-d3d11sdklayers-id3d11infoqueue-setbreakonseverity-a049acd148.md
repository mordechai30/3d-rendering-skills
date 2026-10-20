Source: [https://learn.microsoft.com/en-us/windows/win32/api/D3D11SDKLayers/nf-d3d11sdklayers-id3d11infoqueue-setbreakonseverity](<https://learn.microsoft.com/en-us/windows/win32/api/D3D11SDKLayers/nf-d3d11sdklayers-id3d11infoqueue-setbreakonseverity>)

# ID3D11InfoQueue::SetBreakOnSeverity


## -description

Set a message severity level to break on when a message with that severity level passes through the storage filter.

## -parameters

### -param Severity [in]

Type: <b><a href="/windows/desktop/api/d3d11sdklayers/ne-d3d11sdklayers-d3d11_message_severity">D3D11_MESSAGE_SEVERITY</a></b>

A <a href="/windows/desktop/api/d3d11sdklayers/ne-d3d11sdklayers-d3d11_message_severity">D3D11_MESSAGE_SEVERITY</a>, which represents a message severity level to break on.

### -param bEnable [in]

Type: <b><a href="/windows/desktop/WinProg/windows-data-types">BOOL</a></b>

Turns this breaking condition on or off (true for on, false for off).

## -returns

Type: <b><a href="/windows/win32/com/structure-of-com-error-codes">HRESULT</a></b>

This method returns one of the following <a href="/windows/desktop/direct3d11/d3d11-graphics-reference-returnvalues">Direct3D 11 Return Codes</a>.

## -see-also

<a href="/windows/desktop/api/d3d11sdklayers/nn-d3d11sdklayers-id3d11infoqueue">ID3D11InfoQueue Interface</a>