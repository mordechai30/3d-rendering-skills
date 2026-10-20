Source: [https://learn.microsoft.com/en-us/windows/win32/api/D3D11SDKLayers/ns-d3d11sdklayers-d3d11_info_queue_filter_desc](<https://learn.microsoft.com/en-us/windows/win32/api/D3D11SDKLayers/ns-d3d11sdklayers-d3d11_info_queue_filter_desc>)

# D3D11_INFO_QUEUE_FILTER_DESC structure


## -description

Allow or deny certain types of messages to pass through a filter.

## -struct-fields

### -field NumCategories

Type: <b><a href="/windows/desktop/WinProg/windows-data-types">UINT</a></b>

Number of message categories to allow or deny.

### -field pCategoryList

Type: <b><a href="/windows/desktop/api/d3d11sdklayers/ne-d3d11sdklayers-d3d11_message_category">D3D11_MESSAGE_CATEGORY</a>*</b>

Array of message categories to allow or deny. Array must have at least NumCategories members (see <a href="/windows/desktop/api/d3d11sdklayers/ne-d3d11sdklayers-d3d11_message_category">D3D11_MESSAGE_CATEGORY</a>).

### -field NumSeverities

Type: <b><a href="/windows/desktop/WinProg/windows-data-types">UINT</a></b>

Number of message severity levels to allow or deny.

### -field pSeverityList

Type: <b><a href="/windows/desktop/api/d3d11sdklayers/ne-d3d11sdklayers-d3d11_message_severity">D3D11_MESSAGE_SEVERITY</a>*</b>

Array of message severity levels to allow or deny. Array must have at least NumSeverities members (see <a href="/windows/desktop/api/d3d11sdklayers/ne-d3d11sdklayers-d3d11_message_severity">D3D11_MESSAGE_SEVERITY</a>).

### -field NumIDs

Type: <b><a href="/windows/desktop/WinProg/windows-data-types">UINT</a></b>

Number of message IDs to allow or deny.

### -field pIDList

Type: <b><a href="/windows/desktop/api/d3d11sdklayers/ne-d3d11sdklayers-d3d11_message_id">D3D11_MESSAGE_ID</a>*</b>

Array of message IDs to allow or deny. Array must have at least NumIDs members (see <a href="/windows/desktop/api/d3d11sdklayers/ne-d3d11sdklayers-d3d11_message_id">D3D11_MESSAGE_ID</a>).

## -see-also

<a href="/windows/desktop/direct3d11/d3d11-graphics-reference-d3d11-core-structures">Core Structures</a>



<a href="/windows/desktop/direct3d11/d3d11-graphics-reference-d3d11-layer-structures">Layer Structures</a>