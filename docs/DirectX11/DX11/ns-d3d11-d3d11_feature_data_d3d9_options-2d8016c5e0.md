Source: [https://learn.microsoft.com/en-us/windows/win32/api/D3D11/ns-d3d11-d3d11_feature_data_d3d9_options](<https://learn.microsoft.com/en-us/windows/win32/api/D3D11/ns-d3d11-d3d11_feature_data_d3d9_options>)

# D3D11_FEATURE_DATA_D3D9_OPTIONS structure


## -description

<div class="alert"><b>Note</b>  This structure is supported by the Direct3D 11.1 runtime, which is available on Windows 8 and later operating systems.</div><div> </div>Describes Direct3D 9 feature options in the current graphics driver.

## -struct-fields

### -field FullNonPow2TextureSupport

Specifies whether the driver supports the nonpowers-of-2-unconditionally feature. For more information about this feature, see <a href="/windows/desktop/direct3d11/overviews-direct3d-11-devices-downlevel-intro">feature level</a>. The runtime sets this member to <b>TRUE</b> for hardware at Direct3D 10 and higher feature levels.  For hardware at Direct3D 9.3 and lower feature levels, the runtime sets this member to <b>FALSE</b> if the hardware and driver support the powers-of-2 (2D textures must have widths and heights specified as powers of two) feature or the nonpowers-of-2-conditionally feature. For more information about this feature, see feature level.

## -see-also

<a href="/windows/desktop/direct3d11/d3d11-graphics-reference-d3d11-core-structures">Core Structures</a>



<a href="/windows/desktop/api/d3d11/ne-d3d11-d3d11_feature">D3D11_FEATURE</a>