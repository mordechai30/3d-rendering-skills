Source: [https://learn.microsoft.com/en-us/windows/win32/api/D3D11/ns-d3d11-d3d11_feature_data_d3d11_options2](<https://learn.microsoft.com/en-us/windows/win32/api/D3D11/ns-d3d11-d3d11_feature_data_d3d11_options2>)

# D3D11_FEATURE_DATA_D3D11_OPTIONS2 structure


## -description

Describes Direct3D 11.3 feature options in the current graphics driver.

## -struct-fields

### -field PSSpecifiedStencilRefSupported

Specifies whether the hardware and driver support <b>PSSpecifiedStencilRef</b>.
            The runtime sets this member to <b>TRUE</b> if the hardware and driver support this option.

### -field TypedUAVLoadAdditionalFormats

Specifies whether the hardware and driver support <b>TypedUAVLoadAdditionalFormats</b>.
            The runtime sets this member to <b>TRUE</b> if the hardware and driver support this option.

### -field ROVsSupported

Specifies whether the hardware and driver support ROVs.
            The runtime sets this member to <b>TRUE</b> if the hardware and driver support this option.

### -field ConservativeRasterizationTier

Specifies whether the hardware and driver support conservative rasterization.
            The runtime sets this member to a <a href="/windows/desktop/api/d3d11/ne-d3d11-d3d11_conservative_rasterization_tier">D3D11_CONSERVATIVE_RASTERIZATION_TIER</a>-typed value that indicates if the hardware and driver support conservative rasterization and at what tier level.

### -field TiledResourcesTier

Specifies whether the hardware and driver support tiled resources.
            The runtime sets this member to a <a href="/windows/desktop/api/d3d11/ne-d3d11-d3d11_tiled_resources_tier">D3D11_TILED_RESOURCES_TIER</a>-typed value that indicates if the hardware and driver support tiled resources and at what tier level.

### -field MapOnDefaultTextures

Specifies whether the hardware and driver support mapping on default textures.
            The runtime sets this member to <b>TRUE</b> if the hardware and driver support this option.

### -field StandardSwizzle

Specifies whether the hardware and driver support standard swizzle.
            The runtime sets this member to <b>TRUE</b> if the hardware and driver support this option.

### -field UnifiedMemoryArchitecture

Specifies whether the hardware and driver support Unified Memory Architecture.
            The runtime sets this member to <b>TRUE</b> if the hardware and driver support this option.

## -remarks

If <b>MapOnDefaultTextures</b> is TRUE, applications may create textures using D3D11_USAGE_DEFAULT in combination with non-zero a D3D11_CPU_ACCESS_FLAG value.
        For performance reasons it is typically undesirable to create a default texture with CPU access flags unless the <b>UnifiedMemoryArchitecture</b> option is TRUE, or CPU / GPU usage of the texture is tightly interleaved.
      

Default textures may not be in a mapped state while either bound to the pipeline to referenced by an operation issued to a context.
        Default textures may not be mapped by a deferred context.
        Default textures may not be created shareable.
      

See <a href="/windows/desktop/api/d3d11_3/ne-d3d11_3-d3d11_texture_layout">D3D11_TEXTURE_LAYOUT</a> for texture swizzle options and restrictions.

## -see-also

<a href="/windows/desktop/direct3d11/d3d11-graphics-reference-d3d11-core-structures">Core Structures</a>