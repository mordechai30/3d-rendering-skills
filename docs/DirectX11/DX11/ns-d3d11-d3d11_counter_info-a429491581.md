Source: [https://learn.microsoft.com/en-us/windows/win32/api/D3D11/ns-d3d11-d3d11_counter_info](<https://learn.microsoft.com/en-us/windows/win32/api/D3D11/ns-d3d11-d3d11_counter_info>)

# D3D11_COUNTER_INFO structure


## -description

Information about the video card's performance counter capabilities.

## -struct-fields

### -field LastDeviceDependentCounter

Type: <b><a href="/windows/desktop/api/d3d11/ne-d3d11-d3d11_counter">D3D11_COUNTER</a></b>

Largest device-dependent counter ID that the device supports. If none are supported, this value will be 0. Otherwise it will be greater than or equal to D3D11_COUNTER_DEVICE_DEPENDENT_0. See <a href="/windows/desktop/api/d3d11/ne-d3d11-d3d11_counter">D3D11_COUNTER</a>.

### -field NumSimultaneousCounters

Type: <b><a href="/windows/desktop/WinProg/windows-data-types">UINT</a></b>

Number of counters that can be simultaneously supported.

### -field NumDetectableParallelUnits

Type: <b>UINT8</b>

Number of detectable parallel units that the counter is able to discern. Values are 1 ~ 4. Use NumDetectableParallelUnits to interpret the values of the VERTEX_PROCESSING, GEOMETRY_PROCESSING, PIXEL_PROCESSING, and OTHER_GPU_PROCESSING counters.

## -remarks

This structure is returned by <a href="/windows/desktop/api/d3d11/nf-d3d11-id3d11device-checkcounterinfo">ID3D11Device::CheckCounterInfo</a>.

## -see-also

<a href="/windows/desktop/direct3d11/d3d11-graphics-reference-d3d11-core-structures">Core Structures</a>