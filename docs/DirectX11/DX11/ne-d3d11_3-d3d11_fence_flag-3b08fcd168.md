Source: [https://learn.microsoft.com/en-us/windows/win32/api/d3d11_3/ne-d3d11_3-d3d11_fence_flag](<https://learn.microsoft.com/en-us/windows/win32/api/d3d11_3/ne-d3d11_3-d3d11_fence_flag>)

# D3D11_FENCE_FLAG enumeration


## -description

Specifies fence options.

## -enum-fields

### -field D3D11_FENCE_FLAG_NONE:0

No options are specified.

### -field D3D11_FENCE_FLAG_SHARED:0x2

The fence is shared.

### -field D3D11_FENCE_FLAG_SHARED_CROSS_ADAPTER:0x4

The fence is shared with another GPU adapter.

### -field D3D11_FENCE_FLAG_NON_MONITORED:0x8

## -remarks

This enum is used by the <a href="/windows/desktop/api/d3d11_4/nf-d3d11_4-id3d11device5-createfence">ID3D11Device::CreateFence</a> method.

## -see-also

<a href="/windows/desktop/direct3d11/d3d11-graphics-reference-d3d11-core-enums">Core Enumerations</a>