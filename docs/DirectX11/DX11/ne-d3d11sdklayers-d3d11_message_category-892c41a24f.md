Source: [https://learn.microsoft.com/en-us/windows/win32/api/D3D11SDKLayers/ne-d3d11sdklayers-d3d11_message_category](<https://learn.microsoft.com/en-us/windows/win32/api/D3D11SDKLayers/ne-d3d11sdklayers-d3d11_message_category>)

# D3D11_MESSAGE_CATEGORY enumeration


## -description

Categories of debug messages. This will identify the category of a message when retrieving a message with <a href="/windows/desktop/api/d3d11sdklayers/nf-d3d11sdklayers-id3d11infoqueue-getmessage">ID3D11InfoQueue::GetMessage</a> and when adding a message with <a href="/windows/desktop/api/d3d11sdklayers/nf-d3d11sdklayers-id3d11infoqueue-addmessage">ID3D11InfoQueue::AddMessage</a>. When creating an <a href="/windows/desktop/api/d3d11sdklayers/ns-d3d11sdklayers-d3d11_info_queue_filter">info queue filter</a>, these values can be used to allow or deny any categories of messages to pass through the storage and retrieval filters.

## -enum-fields

### -field D3D11_MESSAGE_CATEGORY_APPLICATION_DEFINED:0

User defined message. See <a href="/windows/desktop/api/d3d11sdklayers/nf-d3d11sdklayers-id3d11infoqueue-addmessage">ID3D11InfoQueue::AddMessage</a>.

### -field D3D11_MESSAGE_CATEGORY_MISCELLANEOUS

### -field D3D11_MESSAGE_CATEGORY_INITIALIZATION

### -field D3D11_MESSAGE_CATEGORY_CLEANUP

### -field D3D11_MESSAGE_CATEGORY_COMPILATION

### -field D3D11_MESSAGE_CATEGORY_STATE_CREATION

### -field D3D11_MESSAGE_CATEGORY_STATE_SETTING

### -field D3D11_MESSAGE_CATEGORY_STATE_GETTING

### -field D3D11_MESSAGE_CATEGORY_RESOURCE_MANIPULATION

### -field D3D11_MESSAGE_CATEGORY_EXECUTION

### -field D3D11_MESSAGE_CATEGORY_SHADER

<b>Direct3D 11:  </b>This value is not supported until Direct3D 11.1.

## -remarks

This is part of the Information Queue feature. See <a href="/windows/desktop/api/d3d11sdklayers/nn-d3d11sdklayers-id3d11infoqueue">ID3D11InfoQueue Interface</a>.

## -see-also

<a href="/windows/desktop/direct3d11/d3d11-graphics-reference-d3d11-layer-enums">Layer Enumerations</a>