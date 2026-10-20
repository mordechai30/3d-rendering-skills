Source: [https://learn.microsoft.com/en-us/windows/win32/api/d3d11/ns-d3d11-d3d11_feature_data_shader_cache](<https://learn.microsoft.com/en-us/windows/win32/api/d3d11/ns-d3d11-d3d11_feature_data_shader_cache>)

# D3D11_FEATURE_DATA_SHADER_CACHE structure


## -description

Describes the level of shader caching supported in the current graphics driver.

## -struct-fields

### -field SupportFlags

Indicates the level of caching supported.

## -remarks

Use this structure with <a href="/windows/desktop/api/d3d11/nf-d3d11-id3d11device-checkfeaturesupport">CheckFeatureSupport</a> to determine the level of support offered for the optional shader-caching features.

See the enumeration constant D3D11_FEATURE_SHADER_CACHE in the <a href="/windows/desktop/api/d3d11/ne-d3d11-d3d11_feature">D3D11_FEATURE</a> enumeration.

## -see-also

<a href="/windows/desktop/direct3d11/d3d11-graphics-reference-d3d11-core-structures">Core Structures</a>