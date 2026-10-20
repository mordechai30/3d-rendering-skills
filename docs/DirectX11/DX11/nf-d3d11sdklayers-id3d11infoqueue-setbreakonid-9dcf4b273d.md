Source: [https://learn.microsoft.com/en-us/windows/win32/api/D3D11SDKLayers/nf-d3d11sdklayers-id3d11infoqueue-setbreakonid](<https://learn.microsoft.com/en-us/windows/win32/api/D3D11SDKLayers/nf-d3d11sdklayers-id3d11infoqueue-setbreakonid>)

# ID3D11InfoQueue::SetBreakOnID


## -description

Set a message identifier to break on when a message with that identifier passes through the storage filter.

## -parameters

### -param ID [in]

Type: <b><a href="/windows/desktop/api/d3d11sdklayers/ne-d3d11sdklayers-d3d11_message_id">D3D11_MESSAGE_ID</a></b>

Message identifier to break on (see <a href="/windows/desktop/api/d3d11sdklayers/ne-d3d11sdklayers-d3d11_message_id">D3D11_MESSAGE_ID</a>).

### -param bEnable [in]

Type: <b><a href="/windows/desktop/WinProg/windows-data-types">BOOL</a></b>

Turns this breaking condition on or off (true for on, false for off).

## -returns

Type: <b><a href="/windows/win32/com/structure-of-com-error-codes">HRESULT</a></b>

This method returns one of the following <a href="/windows/desktop/direct3d11/d3d11-graphics-reference-returnvalues">Direct3D 11 Return Codes</a>.

## -see-also

<a href="/windows/desktop/api/d3d11sdklayers/nn-d3d11sdklayers-id3d11infoqueue">ID3D11InfoQueue Interface</a>