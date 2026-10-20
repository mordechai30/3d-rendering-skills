Source: [https://learn.microsoft.com/en-us/windows/win32/api/D3D11/ns-d3d11-d3d11_feature_data_format_support](<https://learn.microsoft.com/en-us/windows/win32/api/D3D11/ns-d3d11-d3d11_feature_data_format_support>)

# D3D11_FEATURE_DATA_FORMAT_SUPPORT structure


## -description

Describes which resources are supported by the current graphics driver for a given format.

## -struct-fields

### -field InFormat

Type: <b><a href="/windows/desktop/api/dxgiformat/ne-dxgiformat-dxgi_format">DXGI_FORMAT</a></b>


<a href="/windows/desktop/api/dxgiformat/ne-dxgiformat-dxgi_format">DXGI_FORMAT</a> to return information on.

### -field OutFormatSupport

Type: <b><a href="/windows/desktop/WinProg/windows-data-types">UINT</a></b>

Combination of <a href="/windows/desktop/api/d3d11/ne-d3d11-d3d11_format_support">D3D11_FORMAT_SUPPORT</a> flags indicating which resources are supported.

## -see-also

<a href="/windows/desktop/direct3d11/d3d11-graphics-reference-d3d11-core-structures">Core Structures</a>