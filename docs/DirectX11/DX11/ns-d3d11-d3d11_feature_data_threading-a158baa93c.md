Source: [https://learn.microsoft.com/en-us/windows/win32/api/D3D11/ns-d3d11-d3d11_feature_data_threading](<https://learn.microsoft.com/en-us/windows/win32/api/D3D11/ns-d3d11-d3d11_feature_data_threading>)

# D3D11_FEATURE_DATA_THREADING structure


## -description

Describes the multi-threading features that are supported by the current graphics driver.

## -struct-fields

### -field DriverConcurrentCreates

Type: <b><a href="/windows/desktop/WinProg/windows-data-types">BOOL</a></b>

<b>TRUE</b> means resources can be created concurrently on multiple threads while drawing; <b>FALSE</b> means that the presence of coarse synchronization will prevent concurrency.

### -field DriverCommandLists

Type: <b><a href="/windows/desktop/WinProg/windows-data-types">BOOL</a></b>

<b>TRUE</b> means command lists are supported by the current driver; <b>FALSE</b> means that the API will emulate deferred contexts and command lists with software.

## -remarks

Use the D3D11_FEATURE_DATA_THREADING structure with the <a href="/windows/desktop/api/d3d11/nf-d3d11-id3d11device-checkfeaturesupport">ID3D11Device::CheckFeatureSupport</a> method to determine multi-threading support.

## -see-also

<a href="/windows/desktop/direct3d11/d3d11-graphics-reference-d3d11-core-structures">Core Structures</a>