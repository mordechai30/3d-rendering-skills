Source: [https://learn.microsoft.com/en-us/windows/win32/api/D3D11/ns-d3d11-d3d11_feature_data_d3d10_x_hardware_options](<https://learn.microsoft.com/en-us/windows/win32/api/D3D11/ns-d3d11-d3d11_feature_data_d3d10_x_hardware_options>)

# D3D11_FEATURE_DATA_D3D10_X_HARDWARE_OPTIONS structure


## -description

Describes compute shader and raw and structured buffer support in the current graphics driver.

## -struct-fields

### -field ComputeShaders_Plus_RawAndStructuredBuffers_Via_Shader_4_x

Type: <b><a href="/windows/desktop/WinProg/windows-data-types">BOOL</a></b>

<b>TRUE</b> if compute shaders and raw and structured buffers are supported; otherwise <b>FALSE</b>.

## -remarks

Direct3D 11 devices (D3D_FEATURE_LEVEL_11_0) are required to support Compute Shader model 5.0. 
      Direct3D 10.x devices (D3D_FEATURE_LEVEL_10_0, D3D_FEATURE_LEVEL_10_1) can optionally support Compute Shader model 4.0 or 4.1.

## -see-also

<a href="/windows/desktop/direct3d11/d3d11-graphics-reference-d3d11-core-structures">Core Structures</a>