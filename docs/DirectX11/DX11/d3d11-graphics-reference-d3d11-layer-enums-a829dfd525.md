Source: [https://learn.microsoft.com/en-us/windows/win32/direct3d11/d3d11-graphics-reference-d3d11-layer-enums](<https://learn.microsoft.com/en-us/windows/win32/direct3d11/d3d11-graphics-reference-d3d11-layer-enums>)

# Layer Enumerations

This section contains information about the layer enumerations.


## In this section



| Topic                                                                                             | Description                                                                                                                                                                                                                                                                                                                                                                                                                                                                             |
|---------------------------------------------------------------------------------------------------|-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| [**D3D11\_MESSAGE\_CATEGORY**](./ne-d3d11sdklayers-d3d11_message_category-892c41a24f.md)<br/>                             | Categories of debug messages. This will identify the category of a message when retrieving a message with [**ID3D11InfoQueue::GetMessage**](./nf-d3d11sdklayers-id3d11infoqueue-getmessage-2ee9dcb447.md) and when adding a message with [**ID3D11InfoQueue::AddMessage**](./nf-d3d11sdklayers-id3d11infoqueue-addmessage-9e9c8e1a64.md). When creating an [**info queue filter**](./ns-d3d11sdklayers-d3d11_info_queue_filter-2279e19fa7.md), these values can be used to allow or deny any categories of messages to pass through the storage and retrieval filters.<br/> |
| [**D3D11\_MESSAGE\_ID**](./ne-d3d11sdklayers-d3d11_message_id-4971fd618f.md)<br/>                                         | Debug messages for setting up an info-queue filter (see [**D3D11\_INFO\_QUEUE\_FILTER**](./ns-d3d11sdklayers-d3d11_info_queue_filter-2279e19fa7.md)); use these messages to allow or deny message categories to pass through the storage and retrieval filters. These IDs are used by methods such as [**ID3D11InfoQueue::GetMessage**](./nf-d3d11sdklayers-id3d11infoqueue-getmessage-2ee9dcb447.md) or [**ID3D11InfoQueue::AddMessage**](./nf-d3d11sdklayers-id3d11infoqueue-addmessage-9e9c8e1a64.md). <br/>                                                             |
| [**D3D11\_MESSAGE\_SEVERITY**](./ne-d3d11sdklayers-d3d11_message_severity-e4af1c867a.md)<br/>                             | Debug message severity levels for an information queue.<br/>                                                                                                                                                                                                                                                                                                                                                                                                                      |
| [**D3D11\_RLDO\_FLAGS**](./ne-d3d11sdklayers-d3d11_rldo_flags-b1b2404228.md)<br/>                                         | Options for the amount of information to report about a device object's lifetime.<br/>                                                                                                                                                                                                                                                                                                                                                                                            |
| [**D3D11\_SHADER\_TRACKING\_OPTIONS**](./ne-d3d11sdklayers-d3d11_shader_tracking_options-94357982f8.md)<br/>              | Options that specify how to perform shader debug tracking.<br/>                                                                                                                                                                                                                                                                                                                                                                                                                   |
| [**D3D11\_SHADER\_TRACKING\_RESOURCE\_TYPE**](./ne-d3d11sdklayers-d3d11_shader_tracking_resource_type-ebdb8e056a.md)<br/> | Indicates which resource types to track.<br/>                                                                                                                                                                                                                                                                                                                                                                                                                                     |



 

## Related topics

<dl> <dt>

[Layer Reference](./d3d11-graphics-reference-d3d11-layer-e7e5fbf950.md)
</dt> </dl>