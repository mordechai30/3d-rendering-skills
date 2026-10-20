Source: [https://learn.microsoft.com/en-us/windows/win32/api/D3D11/ns-d3d11-d3d11_feature_data_displayable](<https://learn.microsoft.com/en-us/windows/win32/api/D3D11/ns-d3d11-d3d11_feature_data_displayable>)

## -description

Describes the level of displayable surfaces supported in the current graphics driver. See [Displayable surfaces](./displayable-surfaces-447871f193.md).

## -struct-fields

### -field DisplayableTexture

Type: **[BOOL](/windows/win32/winprog/windows-data-types)**

`true` if the driver supports displayable surfaces; otherwise, `false`.

### -field SharedResourceTier

Type: **[D3D11_SHARED_RESOURCE_TIER](./ne-d3d11-d3d11_shared_resource_tier-cfb472b827.md)**

The level of support for shared resources in the current graphics driver.

## -remarks

## -see-also

* [Displayable surfaces](./displayable-surfaces-447871f193.md)