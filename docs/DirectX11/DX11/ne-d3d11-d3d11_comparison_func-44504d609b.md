Source: [https://learn.microsoft.com/en-us/windows/win32/api/D3D11/ne-d3d11-d3d11_comparison_func](<https://learn.microsoft.com/en-us/windows/win32/api/D3D11/ne-d3d11-d3d11_comparison_func>)

# D3D11_COMPARISON_FUNC enumeration


## -description

Comparison options.

## -enum-fields

### -field D3D11_COMPARISON_NEVER:1

Never pass the comparison.

### -field D3D11_COMPARISON_LESS:2

If the source data is less than the destination data, the comparison passes.

### -field D3D11_COMPARISON_EQUAL:3

If the source data is equal to the destination data, the comparison passes.

### -field D3D11_COMPARISON_LESS_EQUAL:4

If the source data is less than or equal to the destination data, the comparison passes.

### -field D3D11_COMPARISON_GREATER:5

If the source data is greater than the destination data, the comparison passes.

### -field D3D11_COMPARISON_NOT_EQUAL:6

If the source data is not equal to the destination data, the comparison passes.

### -field D3D11_COMPARISON_GREATER_EQUAL:7

If the source data is greater than or equal to the destination data, the comparison passes.

### -field D3D11_COMPARISON_ALWAYS:8

Always pass the comparison.

## -remarks

A comparison option determines whether how the runtime compares source (new) data against destination (existing) data before storing the new data. The comparison option is declared in a description before an object is created. The API allows you to set a comparison option for a depth-stencil buffer (see <a href="/windows/desktop/api/d3d11/ns-d3d11-d3d11_depth_stencil_desc">D3D11_DEPTH_STENCIL_DESC</a>), depth-stencil operations (see <a href="/windows/desktop/api/d3d11/ns-d3d11-d3d11_depth_stencilop_desc">D3D11_DEPTH_STENCILOP_DESC</a>), or sampler state (see <a href="/windows/desktop/api/d3d11/ns-d3d11-d3d11_sampler_desc">D3D11_SAMPLER_DESC</a>).

## -see-also

<a href="/windows/desktop/direct3d11/d3d11-graphics-reference-d3d11-core-enums">Core Enumerations</a>