Source: [https://learn.microsoft.com/en-us/windows/win32/api/D3D11SDKLayers/ne-d3d11sdklayers-d3d11_message_severity](<https://learn.microsoft.com/en-us/windows/win32/api/D3D11SDKLayers/ne-d3d11sdklayers-d3d11_message_severity>)

# D3D11_MESSAGE_SEVERITY enumeration


## -description

Debug message severity levels for an information queue.

## -enum-fields

### -field D3D11_MESSAGE_SEVERITY_CORRUPTION:0

Defines some type of corruption which has occurred.

### -field D3D11_MESSAGE_SEVERITY_ERROR

Defines an error message.

### -field D3D11_MESSAGE_SEVERITY_WARNING

Defines a warning message.

### -field D3D11_MESSAGE_SEVERITY_INFO

Defines an information message.

### -field D3D11_MESSAGE_SEVERITY_MESSAGE

Defines a message other than corruption, error, warning, or information.

<b>Direct3D 11:  </b>This value is not supported until Direct3D 11.1.

## -remarks

Use these values to allow or deny message categories to pass through the storage and retrieval filters for an information queue (see <a href="/windows/desktop/api/d3d11sdklayers/ns-d3d11sdklayers-d3d11_info_queue_filter">D3D11_INFO_QUEUE_FILTER</a>). This API is used by <a href="/windows/desktop/api/d3d11sdklayers/nf-d3d11sdklayers-id3d11infoqueue-addapplicationmessage">ID3D11InfoQueue::AddApplicationMessage</a>.

## -see-also

<a href="/windows/desktop/direct3d11/d3d11-graphics-reference-d3d11-layer-enums">Layer Enumerations</a>