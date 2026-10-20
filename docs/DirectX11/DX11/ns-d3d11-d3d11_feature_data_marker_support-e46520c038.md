Source: [https://learn.microsoft.com/en-us/windows/win32/api/D3D11/ns-d3d11-d3d11_feature_data_marker_support](<https://learn.microsoft.com/en-us/windows/win32/api/D3D11/ns-d3d11-d3d11_feature_data_marker_support>)

# D3D11_FEATURE_DATA_MARKER_SUPPORT structure


## -description

<div class="alert"><b>Note</b>  This structure is supported by the Direct3D 11.2 runtime, which is available on Windows 8.1 and later operating systems.</div><div> </div>Describes whether a GPU profiling technique is supported.

## -struct-fields

### -field Profile

Specifies whether the hardware and driver support a GPU profiling technique that can be used with development tools. The runtime sets this member to <b>TRUE</b> if  the hardware and driver support data marking.

## -remarks

If the Direct3D API is the Direct3D 11.2 runtime and can support 11.2 features, <a href="/windows/desktop/api/d3d11/nf-d3d11-id3d11device-checkfeaturesupport">ID3D11Device::CheckFeatureSupport</a> for <b>D3D11_FEATURE_MARKER_SUPPORT</b> will return a SUCCESS code when valid parameters are passed. The <b>Profile</b> member of <b>D3D11_FEATURE_DATA_MARKER_SUPPORT</b> will be set to <b>TRUE</b> or <b>FALSE</b>.

## -see-also

<a href="/windows/desktop/direct3d11/d3d11-graphics-reference-d3d11-core-structures">Core Structures</a>



<a href="/windows/desktop/api/d3d11/ne-d3d11-d3d11_feature">D3D11_FEATURE</a>