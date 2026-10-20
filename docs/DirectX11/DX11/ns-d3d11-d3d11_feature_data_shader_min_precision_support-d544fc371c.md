Source: [https://learn.microsoft.com/en-us/windows/win32/api/D3D11/ns-d3d11-d3d11_feature_data_shader_min_precision_support](<https://learn.microsoft.com/en-us/windows/win32/api/D3D11/ns-d3d11-d3d11_feature_data_shader_min_precision_support>)

# D3D11_FEATURE_DATA_SHADER_MIN_PRECISION_SUPPORT structure


## -description

<div class="alert"><b>Note</b>  This structure is supported by the Direct3D 11.1 runtime, which is available on Windows 8 and later operating systems.</div><div> </div>Describes precision support  options for shaders in the current graphics driver.

## -struct-fields

### -field PixelShaderMinPrecision

A combination of <a href="/windows/desktop/api/d3d11/ne-d3d11-d3d11_shader_min_precision_support">D3D11_SHADER_MIN_PRECISION_SUPPORT</a>-typed values that are combined by using a bitwise OR operation. The resulting value specifies minimum precision levels that the driver supports for the pixel shader. A value of zero indicates that the driver supports only full 32-bit precision for the pixel shader.

### -field AllOtherShaderStagesMinPrecision

A combination of <a href="/windows/desktop/api/d3d11/ne-d3d11-d3d11_shader_min_precision_support">D3D11_SHADER_MIN_PRECISION_SUPPORT</a>-typed values that are combined by using a bitwise OR operation. The resulting value specifies minimum precision levels that the driver supports for all other shader stages. A value of zero indicates that the driver supports only full 32-bit precision for all other shader stages.

## -remarks

For hardware at Direct3D 10 and higher <a href="/windows/desktop/direct3d11/overviews-direct3d-11-devices-downlevel-intro">feature levels</a>, the runtime sets both members identically.  For hardware at Direct3D 9.3 and lower feature levels, the runtime can set a lower precision support in the <b>PixelShaderMinPrecision</b> member than the <b>AllOtherShaderStagesMinPrecision</b> member; for 9.3 and lower, all other shader stages represent only the vertex shader.

For more info about HLSL minimum precision, see <a href="/windows/desktop/direct3d11/direct3d-11-1-features">using HLSL minimum precision</a>.

## -see-also

<a href="/windows/desktop/direct3d11/d3d11-graphics-reference-d3d11-core-structures">Core Structures</a>



<a href="/windows/desktop/api/d3d11/ne-d3d11-d3d11_feature">D3D11_FEATURE</a>