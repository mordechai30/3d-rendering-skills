Source: [https://learn.microsoft.com/en-us/windows/win32/api/D3D11SDKLayers/ns-d3d11sdklayers-d3d11_message](<https://learn.microsoft.com/en-us/windows/win32/api/D3D11SDKLayers/ns-d3d11sdklayers-d3d11_message>)

# D3D11_MESSAGE structure


## -description

A debug message in the Information Queue.

## -struct-fields

### -field Category

Type: <b><a href="/windows/desktop/api/d3d11sdklayers/ne-d3d11sdklayers-d3d11_message_category">D3D11_MESSAGE_CATEGORY</a></b>

The category of the message. See <a href="/windows/desktop/api/d3d11sdklayers/ne-d3d11sdklayers-d3d11_message_category">D3D11_MESSAGE_CATEGORY</a>.

### -field Severity

Type: <b><a href="/windows/desktop/api/d3d11sdklayers/ne-d3d11sdklayers-d3d11_message_severity">D3D11_MESSAGE_SEVERITY</a></b>

The severity of the message. See <a href="/windows/desktop/api/d3d11sdklayers/ne-d3d11sdklayers-d3d11_message_severity">D3D11_MESSAGE_SEVERITY</a>.

### -field ID

Type: <b><a href="/windows/desktop/api/d3d11sdklayers/ne-d3d11sdklayers-d3d11_message_id">D3D11_MESSAGE_ID</a></b>

The ID of the message. See <a href="/windows/desktop/api/d3d11sdklayers/ne-d3d11sdklayers-d3d11_message_id">D3D11_MESSAGE_ID</a>.

### -field pDescription

Type: <b>const char*</b>

The message string.

### -field DescriptionByteLength

Type: <b><a href="/windows/desktop/WinProg/windows-data-types">SIZE_T</a></b>

The length of pDescription in bytes.

## -remarks

This structure is returned from <a href="/windows/desktop/api/d3d11sdklayers/nf-d3d11sdklayers-id3d11infoqueue-getmessage">ID3D11InfoQueue::GetMessage</a> as part of the Information Queue feature (see <a href="/windows/desktop/api/d3d11sdklayers/nn-d3d11sdklayers-id3d11infoqueue">ID3D11InfoQueue Interface</a>).

## -see-also

<a href="/windows/desktop/direct3d11/d3d11-graphics-reference-d3d11-core-structures">Core Structures</a>



<a href="/windows/desktop/direct3d11/d3d11-graphics-reference-d3d11-layer-structures">Layer Structures</a>