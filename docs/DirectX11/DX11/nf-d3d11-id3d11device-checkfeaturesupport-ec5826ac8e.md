Source: [https://learn.microsoft.com/en-us/windows/win32/api/D3D11/nf-d3d11-id3d11device-checkfeaturesupport](<https://learn.microsoft.com/en-us/windows/win32/api/D3D11/nf-d3d11-id3d11device-checkfeaturesupport>)

# ID3D11Device::CheckFeatureSupport


## -description

Gets information about the features that are supported by the current graphics driver.

## -parameters

### -param Feature

Type: <b><a href="/windows/desktop/api/d3d11/ne-d3d11-d3d11_feature">D3D11_FEATURE</a></b>

A member of the <a href="/windows/desktop/api/d3d11/ne-d3d11-d3d11_feature">D3D11_FEATURE</a> enumerated type that describes which feature to query for support.

### -param pFeatureSupportData [out]

Type: <b>void*</b>

Upon completion of the method, the passed structure is filled with data that describes the feature support.

### -param FeatureSupportDataSize

Type: <b><a href="/windows/desktop/WinProg/windows-data-types">UINT</a></b>

The size of the structure passed to the <i>pFeatureSupportData</i> parameter.

## -returns

Type: <b><a href="/windows/win32/com/structure-of-com-error-codes">HRESULT</a></b>

Returns S_OK if successful; otherwise, returns E_INVALIDARG if an unsupported data type is passed to the <i>pFeatureSupportData</i> parameter 
      or a size mismatch is detected for the <i>FeatureSupportDataSize</i> parameter.

## -remarks

To query for multi-threading support, pass the <b>D3D11_FEATURE_THREADING</b> value to the <i>Feature</i> parameter, pass 
      the <a href="/windows/desktop/api/d3d11/ns-d3d11-d3d11_feature_data_threading">D3D11_FEATURE_DATA_THREADING</a> structure to the  <i>pFeatureSupportData</i> parameter, and pass the size of 
      the <b>D3D11_FEATURE_DATA_THREADING</b> structure to the <i>FeatureSupportDataSize</i> parameter.

Calling CheckFeatureSupport with <i>Feature</i> set to D3D11_FEATURE_FORMAT_SUPPORT causes the method to return the same information that would be returned 
      by <a href="/windows/desktop/api/d3d11/nf-d3d11-id3d11device-checkformatsupport">ID3D11Device::CheckFormatSupport</a>.

## -see-also

<a href="/windows/desktop/api/d3d11/nn-d3d11-id3d11device">ID3D11Device</a>