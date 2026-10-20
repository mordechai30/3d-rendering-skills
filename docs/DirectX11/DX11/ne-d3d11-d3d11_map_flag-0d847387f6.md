Source: [https://learn.microsoft.com/en-us/windows/win32/api/D3D11/ne-d3d11-d3d11_map_flag](<https://learn.microsoft.com/en-us/windows/win32/api/D3D11/ne-d3d11-d3d11_map_flag>)

# D3D11_MAP_FLAG enumeration


## -description

Specifies how the CPU should respond when an application calls the <a href="/windows/desktop/api/d3d11/nf-d3d11-id3d11devicecontext-map">ID3D11DeviceContext::Map</a> method on a resource that is being used by the GPU.

## -enum-fields

### -field D3D11_MAP_FLAG_DO_NOT_WAIT:0x100000L

Specifies that <a href="/windows/desktop/api/d3d11/nf-d3d11-id3d11devicecontext-map">ID3D11DeviceContext::Map</a> should return DXGI_ERROR_WAS_STILL_DRAWING when the GPU blocks the CPU from accessing a resource. For more information about this error code, see <a href="/windows/desktop/direct3ddxgi/dxgi-error">DXGI_ERROR</a>.

## -remarks

This enumeration is used by <a href="/windows/desktop/api/d3d11/nf-d3d11-id3d11devicecontext-map">ID3D11DeviceContext::Map</a>.

D3D11_MAP_FLAG_DO_NOT_WAIT cannot be used with <a href="/windows/desktop/api/d3d11/ne-d3d11-d3d11_map">D3D11_MAP_WRITE_DISCARD</a> or <a href="/windows/desktop/api/d3d11/ne-d3d11-d3d11_map">D3D11_MAP_WRITE_NOOVERWRITE</a>.

## -see-also

<a href="/windows/desktop/direct3d11/d3d11-graphics-reference-resource-enums">Resource Enumerations</a>