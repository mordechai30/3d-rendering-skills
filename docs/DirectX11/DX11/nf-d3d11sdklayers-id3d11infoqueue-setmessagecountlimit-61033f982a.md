Source: [https://learn.microsoft.com/en-us/windows/win32/api/D3D11SDKLayers/nf-d3d11sdklayers-id3d11infoqueue-setmessagecountlimit](<https://learn.microsoft.com/en-us/windows/win32/api/D3D11SDKLayers/nf-d3d11sdklayers-id3d11infoqueue-setmessagecountlimit>)

# ID3D11InfoQueue::SetMessageCountLimit


## -description

Set the maximum number of messages that can be added to the message queue.

## -parameters

### -param MessageCountLimit [in]

Type: <b><a href="/windows/desktop/WinProg/windows-data-types">UINT64</a></b>

Maximum number of messages that can be added to the message queue. -1 means no limit.

## -returns

Type: <b><a href="/windows/win32/com/structure-of-com-error-codes">HRESULT</a></b>

This method returns one of the following <a href="/windows/desktop/direct3d11/d3d11-graphics-reference-returnvalues">Direct3D 11 Return Codes</a>.

## -remarks

When the number of messages in the message queue has reached the maximum limit, new messages coming in will push old messages out.

## -see-also

<a href="/windows/desktop/api/d3d11sdklayers/nn-d3d11sdklayers-id3d11infoqueue">ID3D11InfoQueue Interface</a>