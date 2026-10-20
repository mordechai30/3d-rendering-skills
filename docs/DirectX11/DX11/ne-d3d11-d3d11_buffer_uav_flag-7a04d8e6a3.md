Source: [https://learn.microsoft.com/en-us/windows/win32/api/D3D11/ne-d3d11-d3d11_buffer_uav_flag](<https://learn.microsoft.com/en-us/windows/win32/api/D3D11/ne-d3d11-d3d11_buffer_uav_flag>)

# D3D11_BUFFER_UAV_FLAG enumeration


## -description

Identifies unordered-access view options for a buffer resource.

## -enum-fields

### -field D3D11_BUFFER_UAV_FLAG_RAW:0x1

Resource contains raw, unstructured data.  Requires the UAV format to be DXGI_FORMAT_R32_TYPELESS.
        For more info about raw viewing of buffers, see <a href="/windows/desktop/direct3d11/overviews-direct3d-11-resources-intro">Raw Views of Buffers</a>.

### -field D3D11_BUFFER_UAV_FLAG_APPEND:0x2

Allow data to be appended to the end of the buffer.  <b>D3D11_BUFFER_UAV_FLAG_APPEND</b> flag must also be used for 
        any view that will be used as a <a href="/windows/desktop/direct3dhlsl/sm5-object-appendstructuredbuffer">AppendStructuredBuffer</a> or a <a href="/windows/desktop/direct3dhlsl/sm5-object-consumestructuredbuffer">ConsumeStructuredBuffer</a>. 
        Requires the UAV format to be DXGI_FORMAT_UNKNOWN.

### -field D3D11_BUFFER_UAV_FLAG_COUNTER:0x4

Adds a counter to the unordered-access-view buffer.  <b>D3D11_BUFFER_UAV_FLAG_COUNTER</b> can only be used on a UAV that is a 
        <a href="/windows/desktop/direct3dhlsl/sm5-object-rwstructuredbuffer">RWStructuredBuffer</a> and it enables the functionality needed for the <a href="/windows/desktop/direct3dhlsl/sm5-object-rwstructuredbuffer-incrementcounter">IncrementCounter</a> and <a href="/windows/desktop/direct3dhlsl/sm5-object-rwstructuredbuffer-decrementcounter">DecrementCounter</a> methods in HLSL. Requires the UAV format to be DXGI_FORMAT_UNKNOWN.

## -see-also

<a href="/windows/desktop/direct3d11/d3d11-graphics-reference-d3d11-core-enums">Core Enumerations</a>



<a href="/windows/desktop/direct3d11/d3d11-graphics-reference-resource-enums">Resource Enumerations</a>