Source: [https://learn.microsoft.com/en-us/windows/win32/api/D3D11SDKLayers/nf-d3d11sdklayers-id3d11infoqueue-getnummessagesdiscardedbymessagecountlimit](<https://learn.microsoft.com/en-us/windows/win32/api/D3D11SDKLayers/nf-d3d11sdklayers-id3d11infoqueue-getnummessagesdiscardedbymessagecountlimit>)

# ID3D11InfoQueue::GetNumMessagesDiscardedByMessageCountLimit


## -description

Get the number of messages that were discarded due to the message count limit.



## -returns

Type: <b><a href="/windows/desktop/WinProg/windows-data-types">UINT64</a></b>

Number of messages discarded.

## -remarks

Get and set the message count limit with <a href="/windows/desktop/api/d3d11sdklayers/nf-d3d11sdklayers-id3d11infoqueue-getmessagecountlimit">ID3D11InfoQueue::GetMessageCountLimit</a> and <a href="/windows/desktop/api/d3d11sdklayers/nf-d3d11sdklayers-id3d11infoqueue-setmessagecountlimit">ID3D11InfoQueue::SetMessageCountLimit</a>, respectively.

## -see-also

<a href="/windows/desktop/api/d3d11sdklayers/nn-d3d11sdklayers-id3d11infoqueue">ID3D11InfoQueue Interface</a>