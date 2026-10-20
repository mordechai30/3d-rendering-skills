Source: [https://learn.microsoft.com/en-us/windows/win32/api/D3D11SDKLayers/nf-d3d11sdklayers-id3d11infoqueue-getmessagecountlimit](<https://learn.microsoft.com/en-us/windows/win32/api/D3D11SDKLayers/nf-d3d11sdklayers-id3d11infoqueue-getmessagecountlimit>)

# ID3D11InfoQueue::GetMessageCountLimit


## -description

Get the maximum number of messages that can be added to the message queue.



## -returns

Type: <b><a href="/windows/desktop/WinProg/windows-data-types">UINT64</a></b>

Maximum number of messages that can be added to the queue. -1 means no limit.

## -remarks

When the number of messages in the message queue has reached the maximum limit, new messages coming in will push old messages out.

## -see-also

<a href="/windows/desktop/api/d3d11sdklayers/nn-d3d11sdklayers-id3d11infoqueue">ID3D11InfoQueue Interface</a>