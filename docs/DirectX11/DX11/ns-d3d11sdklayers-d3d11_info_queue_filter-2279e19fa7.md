Source: [https://learn.microsoft.com/en-us/windows/win32/api/D3D11SDKLayers/ns-d3d11sdklayers-d3d11_info_queue_filter](<https://learn.microsoft.com/en-us/windows/win32/api/D3D11SDKLayers/ns-d3d11sdklayers-d3d11_info_queue_filter>)

# D3D11_INFO_QUEUE_FILTER structure


## -description

Debug message filter; contains a lists of message types to allow or deny.

## -struct-fields

### -field AllowList

Type: <b><a href="/windows/desktop/api/d3d11sdklayers/ns-d3d11sdklayers-d3d11_info_queue_filter_desc">D3D11_INFO_QUEUE_FILTER_DESC</a></b>

Types of messages that you want to allow. See <a href="/windows/desktop/api/d3d11sdklayers/ns-d3d11sdklayers-d3d11_info_queue_filter_desc">D3D11_INFO_QUEUE_FILTER_DESC</a>.

### -field DenyList

Type: <b><a href="/windows/desktop/api/d3d11sdklayers/ns-d3d11sdklayers-d3d11_info_queue_filter_desc">D3D11_INFO_QUEUE_FILTER_DESC</a></b>

Types of messages that you want to deny.

## -remarks

For use with an <a href="/windows/desktop/api/d3d11sdklayers/nn-d3d11sdklayers-id3d11infoqueue">ID3D11InfoQueue Interface</a>.

## -see-also

<a href="/windows/desktop/direct3d11/d3d11-graphics-reference-d3d11-core-structures">Core Structures</a>



<a href="/windows/desktop/direct3d11/d3d11-graphics-reference-d3d11-layer-structures">Layer Structures</a>