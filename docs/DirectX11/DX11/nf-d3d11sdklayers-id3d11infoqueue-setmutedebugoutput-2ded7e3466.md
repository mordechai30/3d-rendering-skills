Source: [https://learn.microsoft.com/en-us/windows/win32/api/D3D11SDKLayers/nf-d3d11sdklayers-id3d11infoqueue-setmutedebugoutput](<https://learn.microsoft.com/en-us/windows/win32/api/D3D11SDKLayers/nf-d3d11sdklayers-id3d11infoqueue-setmutedebugoutput>)

# ID3D11InfoQueue::SetMuteDebugOutput


## -description

Set a boolean that turns the debug output on or off.

## -parameters

### -param bMute [in]

Type: <b><a href="/windows/desktop/WinProg/windows-data-types">BOOL</a></b>

Disable/Enable the debug output (<b>TRUE</b> to disable or mute the output, <b>FALSE</b> to enable the output).

## -remarks

This will stop messages that pass the storage filter from being printed out in the debug output, however those messages will still be added to the message queue.

## -see-also

<a href="/windows/desktop/api/d3d11sdklayers/nn-d3d11sdklayers-id3d11infoqueue">ID3D11InfoQueue Interface</a>