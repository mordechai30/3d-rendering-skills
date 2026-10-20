Source: [https://learn.microsoft.com/en-us/windows/win32/api/D3D11_2/nf-d3d11_2-id3d11device2-checkmultisamplequalitylevels1](<https://learn.microsoft.com/en-us/windows/win32/api/D3D11_2/nf-d3d11_2-id3d11device2-checkmultisamplequalitylevels1>)

# ID3D11Device2::CheckMultisampleQualityLevels1


## -description

Get the number of quality levels available during multisampling.

## -parameters

### -param Format [in]

Type: <b><a href="/windows/desktop/api/dxgiformat/ne-dxgiformat-dxgi_format">DXGI_FORMAT</a></b>

The texture format during multisampling.

### -param SampleCount [in]

Type: <b><a href="/windows/desktop/WinProg/windows-data-types">UINT</a></b>

The number of samples during multisampling.

### -param Flags [in]

Type: <b><a href="/windows/desktop/WinProg/windows-data-types">UINT</a></b>

A combination of <a href="/windows/desktop/api/d3d11_2/ne-d3d11_2-d3d11_check_multisample_quality_levels_flag">D3D11_CHECK_MULTISAMPLE_QUALITY_LEVELS_FLAGS</a> values that are combined by using a bitwise OR operation. Currently, only <a href="/windows/desktop/api/d3d11_2/ne-d3d11_2-d3d11_check_multisample_quality_levels_flag">D3D11_CHECK_MULTISAMPLE_QUALITY_LEVELS_TILED_RESOURCE</a> is supported.

### -param pNumQualityLevels [out]

Type: <b><a href="/windows/desktop/WinProg/windows-data-types">UINT</a>*</b>

A pointer to a variable the receives the number of quality levels supported by the adapter. See Remarks.

## -returns

Type: <b><a href="/windows/win32/com/structure-of-com-error-codes">HRESULT</a></b>

This method returns one of the <a href="/windows/desktop/direct3d11/d3d11-graphics-reference-returnvalues">Direct3D 11 Return Codes</a>.

## -remarks

When you multisample a texture, the number of quality levels available for an adapter is dependent on the texture format that you use and the number of 
      samples that you request. The maximum number of quality levels is defined by <b>D3D11_MAX_MULTISAMPLE_SAMPLE_COUNT</b> in D3D11.h. If this method returns 0, the format 
      and sample count combination is not supported for the installed adapter.

Furthermore, the definition of a quality level is up to each hardware vendor to define, however no facility is provided by Direct3D to help discover 
      this information.

Note that FEATURE_LEVEL_10_1 devices are required to support 4x MSAA for all render targets except R32G32B32A32 and R32G32B32.
      FEATURE_LEVEL_11_0 devices are required to support 4x MSAA for all render target formats, and 8x MSAA for all render target formats 
      except R32G32B32A32 formats.

## -see-also

<a href="/windows/desktop/api/d3d11_2/nn-d3d11_2-id3d11device2">ID3D11Device2</a>