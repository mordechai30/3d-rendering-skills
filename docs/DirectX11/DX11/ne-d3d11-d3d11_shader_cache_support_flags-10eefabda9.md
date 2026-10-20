Source: [https://learn.microsoft.com/en-us/windows/win32/api/d3d11/ne-d3d11-d3d11_shader_cache_support_flags](<https://learn.microsoft.com/en-us/windows/win32/api/d3d11/ne-d3d11-d3d11_shader_cache_support_flags>)

# D3D11_SHADER_CACHE_SUPPORT_FLAGS enumeration


## -description

Describes the level of support for shader caching in the current graphics driver.

## -enum-fields

### -field D3D11_SHADER_CACHE_SUPPORT_NONE:0

Indicates that the driver does not support shader caching.

### -field D3D11_SHADER_CACHE_SUPPORT_AUTOMATIC_INPROC_CACHE:0x1

Indicates that the driver supports an OS-managed shader cache that stores compiled shaders in memory during the current run of the application.

### -field D3D11_SHADER_CACHE_SUPPORT_AUTOMATIC_DISK_CACHE:0x2

Indicates that the driver supports an OS-managed shader cache that stores compiled shaders on disk to accelerate future runs of the application.

## -remarks

This enum is used by the [D3D11_FEATURE_DATA_SHADER_CACHE](./ns-d3d11-d3d11_feature_data_shader_cache-c03958b663.md) structure.

## -see-also

[Core structures](./d3d11-graphics-reference-d3d11-core-structures-f8320fb28b.md)