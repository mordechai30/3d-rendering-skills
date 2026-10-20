Source: [https://learn.microsoft.com/en-us/windows/win32/api/D3D11ShaderTracing/ne-d3d11shadertracing-d3d11_trace_gs_input_primitive](<https://learn.microsoft.com/en-us/windows/win32/api/D3D11ShaderTracing/ne-d3d11shadertracing-d3d11_trace_gs_input_primitive>)

# D3D11_TRACE_GS_INPUT_PRIMITIVE enumeration


## -description

Identifies the type of geometry shader input primitive.

## -enum-fields

### -field D3D11_TRACE_GS_INPUT_PRIMITIVE_UNDEFINED:0

Identifies the geometry shader input primitive as undefined.

### -field D3D11_TRACE_GS_INPUT_PRIMITIVE_POINT:1

Identifies the geometry shader input primitive as a point.

### -field D3D11_TRACE_GS_INPUT_PRIMITIVE_LINE:2

Identifies the geometry shader input primitive as a line.

### -field D3D11_TRACE_GS_INPUT_PRIMITIVE_TRIANGLE:3

Identifies the geometry shader input primitive as a triangle.

### -field D3D11_TRACE_GS_INPUT_PRIMITIVE_LINE_ADJ:6

Identifies the geometry shader input primitive as an adjacent line.

### -field D3D11_TRACE_GS_INPUT_PRIMITIVE_TRIANGLE_ADJ:7

Identifies the geometry shader input primitive as an adjacent triangle.

## -remarks

<b>D3D11_TRACE_GS_INPUT_PRIMITIVE</b> identifies the type of geometry shader input primitive in a <a href="/windows/desktop/api/d3d11shadertracing/ns-d3d11shadertracing-d3d11_trace_stats">D3D11_TRACE_STATS</a> structure.

<div class="alert"><b>Note</b>  This API requires the Windows Software Development Kit (SDK) for Windows 8.</div>
<div> </div>

## -see-also

<a href="/windows/desktop/direct3d11/d3d11-graphics-reference-shader-enums">Shader Enumerations</a>