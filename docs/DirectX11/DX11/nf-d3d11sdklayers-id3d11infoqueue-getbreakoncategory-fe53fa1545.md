Source: [https://learn.microsoft.com/en-us/windows/win32/api/D3D11SDKLayers/nf-d3d11sdklayers-id3d11infoqueue-getbreakoncategory](<https://learn.microsoft.com/en-us/windows/win32/api/D3D11SDKLayers/nf-d3d11sdklayers-id3d11infoqueue-getbreakoncategory>)

# ID3D11InfoQueue::GetBreakOnCategory


## -description

Get a message category to break on when a message with that category passes through the storage filter.

## -parameters

### -param Category [in]

Type: <b><a href="/windows/desktop/api/d3d11sdklayers/ne-d3d11sdklayers-d3d11_message_category">D3D11_MESSAGE_CATEGORY</a></b>

Message category to break on (see <a href="/windows/desktop/api/d3d11sdklayers/ne-d3d11sdklayers-d3d11_message_category">D3D11_MESSAGE_CATEGORY</a>).

## -returns

Type: <b><a href="/windows/desktop/WinProg/windows-data-types">BOOL</a></b>

Whether this breaking condition is turned on or off (true for on, false for off).

## -see-also

<a href="/windows/desktop/api/d3d11sdklayers/nn-d3d11sdklayers-id3d11infoqueue">ID3D11InfoQueue Interface</a>