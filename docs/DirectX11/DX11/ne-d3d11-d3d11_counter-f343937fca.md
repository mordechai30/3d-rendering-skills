Source: [https://learn.microsoft.com/en-us/windows/win32/api/D3D11/ne-d3d11-d3d11_counter](<https://learn.microsoft.com/en-us/windows/win32/api/D3D11/ne-d3d11-d3d11_counter>)

# D3D11_COUNTER enumeration


## -description

Options for performance counters.

## -enum-fields

### -field D3D11_COUNTER_DEVICE_DEPENDENT_0:0x40000000

Define a performance counter that is dependent on the hardware device.

## -remarks

Independent hardware vendors may define their own set of performance counters for their devices, by giving the enumeration value a number that is greater than the value for D3D11_COUNTER_DEVICE_DEPENDENT_0.

This enumeration is used by <a href="/windows/desktop/api/d3d11/ns-d3d11-d3d11_counter_desc">D3D11_COUNTER_DESC</a> and <a href="/windows/desktop/api/d3d11/ns-d3d11-d3d11_counter_info">D3D11_COUNTER_INFO</a>.

## -see-also

<a href="/windows/desktop/direct3d11/d3d11-graphics-reference-d3d11-core-enums">Core Enumerations</a>