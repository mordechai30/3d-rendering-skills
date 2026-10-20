Source: [https://learn.microsoft.com/en-us/windows/win32/api/D3D11/ns-d3d11-d3d11_feature_data_d3d9_simple_instancing_support](<https://learn.microsoft.com/en-us/windows/win32/api/D3D11/ns-d3d11-d3d11_feature_data_d3d9_simple_instancing_support>)

# D3D11_FEATURE_DATA_D3D9_SIMPLE_INSTANCING_SUPPORT structure


## -description

<div class="alert"><b>Note</b>  This structure is supported by the Direct3D 11.2 runtime, which is available on Windows 8.1 and later operating systems.
      </div><div> </div>Describes whether simple instancing is supported.

## -struct-fields

### -field SimpleInstancingSupported

Specifies whether the hardware and driver support simple instancing. The runtime sets this member to <b>TRUE</b> if  the hardware and driver support simple instancing.

## -remarks

If the Direct3D API is the Direct3D 11.2 runtime and can support 11.2 features, <a href="/windows/desktop/api/d3d11/nf-d3d11-id3d11device-checkfeaturesupport">ID3D11Device::CheckFeatureSupport</a> for <b>D3D11_FEATURE_D3D9_SIMPLE_INSTANCING_SUPPORT</b> will return a SUCCESS code when valid parameters are passed. The <b>SimpleInstancingSupported</b> member of <b>D3D11_FEATURE_DATA_D3D9_SIMPLE_INSTANCING_SUPPORT</b> will be set to <b>TRUE</b> or <b>FALSE</b>.
      

Simple instancing means that instancing is supported with the caveat that the <b>InstanceDataStepRate</b> member of the <a href="/windows/desktop/api/d3d11/ns-d3d11-d3d11_input_element_desc">D3D11_INPUT_ELEMENT_DESC</a> structure must be equal to 1. This does not change the full instancing support provided by hardware at feature level 9.3 and above, and is meant to expose the instancing support that may be available on feature level 9.2 and 9.1 hardware.

## -see-also

<a href="/windows/desktop/direct3d11/d3d11-graphics-reference-d3d11-core-structures">Core Structures</a>



<a href="/windows/desktop/api/d3d11/ne-d3d11-d3d11_feature">D3D11_FEATURE</a>