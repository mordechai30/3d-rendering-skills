Source: [https://learn.microsoft.com/en-us/windows/win32/api/d3d11/ne-d3d11-d3d11_shared_resource_tier](<https://learn.microsoft.com/en-us/windows/win32/api/d3d11/ne-d3d11-d3d11_shared_resource_tier>)

## -description

Defines constants that specify the level of support for shared resources in the current graphics driver.

## -enum-fields

### -field D3D11_SHARED_RESOURCE_TIER_0:0

Specifies the support available when [D3D11_FEATURE_DATA_D3D11_OPTIONS::ExtendedResourceSharing](./ns-d3d11-d3d11_feature_data_d3d11_options-844c1460d6.md) is `FALSE` (only very old drivers have this value set to `FALSE`).

See [Extended support for shared Texture2D resources](./direct3d-11-1-features-1ee1102fed.md#extended-support-for-shared-texture2d-resources).

### -field D3D11_SHARED_RESOURCE_TIER_1

Specifies the support available when [D3D11_FEATURE_DATA_D3D11_OPTIONS::ExtendedResourceSharing](./ns-d3d11-d3d11_feature_data_d3d11_options-844c1460d6.md) and [D3D11_FEATURE_DATA_D3D11_OPTIONS4::ExtendedNV12SharedTextureSupported](./ns-d3d11_4-d3d11_feature_data_d3d11_options4-c5ec219f7b.md) are `TRUE`.

You can share additional formats; see [Extended support for shared Texture2D resources](./direct3d-11-1-features-1ee1102fed.md#extended-support-for-shared-texture2d-resources).

Only formats that are still shareable when **D3D11_FEATURE_DATA_D3D11_OPTIONS::ExtendedResourceSharing** == `FALSE` can be shared across APIs between Direct3D 11 and Direct3D 12.

Resource formats added by **D3D11_FEATURE_DATA_D3D11_OPTIONS::ExtendedResourceSharing** == `TRUE` can't be shared across APIs.

### -field D3D11_SHARED_RESOURCE_TIER_2

Specifies the support available when [D3D11_FEATURE_DATA_D3D11_OPTIONS4::ExtendedNV12SharedTextureSupported](./ns-d3d11_4-d3d11_feature_data_d3d11_options4-c5ec219f7b.md) is `TRUE`. Also see [Extended NV12 texture support](./direct3d-11-4-features-f2101282e3.md#extended-nv12-texture-support).

See [Extended support for shared Texture2D resources](./direct3d-11-1-features-1ee1102fed.md#extended-support-for-shared-texture2d-resources).

Sharing across APIs between Direct3D 11 and Direct3D 12 is possible for the **D3D11_FEATURE_DATA_D3D11_OPTIONS::ExtendedResourceSharing** == `TRUE` format list.

### -field D3D11_SHARED_RESOURCE_TIER_3

Specifies that [DXGI_FORMAT_R11G11B10_FLOAT](../dxgiformat/ne-dxgiformat-dxgi_format.md) supports NT handle sharing. Also see [CreateSharedHandle](../dxgi1_2/nf-dxgi1_2-idxgiresource1-createsharedhandle.md).

Sharing across APIs between Direct3D 11 and Direct3D 12 is possible for the **DXGI_FORMAT_R11G11B10_FLOAT** format.

## -remarks

## -see-also

* [Extended support for shared Texture2D resources](./direct3d-11-1-features-1ee1102fed.md#extended-support-for-shared-texture2d-resources)