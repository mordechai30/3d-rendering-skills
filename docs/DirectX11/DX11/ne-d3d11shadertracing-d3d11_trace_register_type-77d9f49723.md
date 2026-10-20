Source: [https://learn.microsoft.com/en-us/windows/win32/api/D3D11ShaderTracing/ne-d3d11shadertracing-d3d11_trace_register_type](<https://learn.microsoft.com/en-us/windows/win32/api/D3D11ShaderTracing/ne-d3d11shadertracing-d3d11_trace_register_type>)

# D3D11_TRACE_REGISTER_TYPE enumeration


## -description

Identifies a type of trace register.

## -enum-fields

### -field D3D11_TRACE_OUTPUT_NULL_REGISTER:0

Output <b>NULL</b> register.

### -field D3D11_TRACE_INPUT_REGISTER

Input register.

### -field D3D11_TRACE_INPUT_PRIMITIVE_ID_REGISTER

Input primitive ID register.

### -field D3D11_TRACE_IMMEDIATE_CONSTANT_BUFFER

Immediate constant buffer.

### -field D3D11_TRACE_TEMP_REGISTER

Temporary register.

### -field D3D11_TRACE_INDEXABLE_TEMP_REGISTER

Temporary register that can be indexed.

### -field D3D11_TRACE_OUTPUT_REGISTER

Output register.

### -field D3D11_TRACE_OUTPUT_DEPTH_REGISTER

Output oDepth register.

### -field D3D11_TRACE_CONSTANT_BUFFER

Constant buffer.

### -field D3D11_TRACE_IMMEDIATE32

Immediate32 register.

### -field D3D11_TRACE_SAMPLER

Sampler.

### -field D3D11_TRACE_RESOURCE

Resource.

### -field D3D11_TRACE_RASTERIZER

Rasterizer.

### -field D3D11_TRACE_OUTPUT_COVERAGE_MASK

Output coverage mask.

### -field D3D11_TRACE_STREAM

Stream.

### -field D3D11_TRACE_THIS_POINTER

This pointer.

### -field D3D11_TRACE_OUTPUT_CONTROL_POINT_ID_REGISTER

Output control point ID register (this is actually an input; it defines the output that the thread controls).

### -field D3D11_TRACE_INPUT_FORK_INSTANCE_ID_REGISTER

Input fork instance ID register.

### -field D3D11_TRACE_INPUT_JOIN_INSTANCE_ID_REGISTER

Input join instance ID register.

### -field D3D11_TRACE_INPUT_CONTROL_POINT_REGISTER

Input control point register.

### -field D3D11_TRACE_OUTPUT_CONTROL_POINT_REGISTER

Output control point register.

### -field D3D11_TRACE_INPUT_PATCH_CONSTANT_REGISTER

Input patch constant register.

### -field D3D11_TRACE_INPUT_DOMAIN_POINT_REGISTER

Input domain point register.

### -field D3D11_TRACE_UNORDERED_ACCESS_VIEW

Unordered-access view.

### -field D3D11_TRACE_THREAD_GROUP_SHARED_MEMORY

Thread group shared memory.

### -field D3D11_TRACE_INPUT_THREAD_ID_REGISTER

Input thread ID register.

### -field D3D11_TRACE_INPUT_THREAD_GROUP_ID_REGISTER

Thread group ID register.

### -field D3D11_TRACE_INPUT_THREAD_ID_IN_GROUP_REGISTER

Input thread ID in-group register.

### -field D3D11_TRACE_INPUT_COVERAGE_MASK_REGISTER

Input coverage mask register.

### -field D3D11_TRACE_INPUT_THREAD_ID_IN_GROUP_FLATTENED_REGISTER

Input thread ID in-group flattened register.

### -field D3D11_TRACE_INPUT_GS_INSTANCE_ID_REGISTER

Input geometry shader (GS) instance ID register.

### -field D3D11_TRACE_OUTPUT_DEPTH_GREATER_EQUAL_REGISTER

Output oDepth greater than or equal register.

### -field D3D11_TRACE_OUTPUT_DEPTH_LESS_EQUAL_REGISTER

Output oDepth less than or equal register.

### -field D3D11_TRACE_IMMEDIATE64

Immediate64 register.

### -field D3D11_TRACE_INPUT_CYCLE_COUNTER_REGISTER

Cycle counter register.

### -field D3D11_TRACE_INTERFACE_POINTER

Interface pointer.

## -remarks

<b>D3D11_TRACE_REGISTER_TYPE</b> identifies the type of trace register in a <a href="/windows/desktop/api/d3d11shadertracing/ns-d3d11shadertracing-d3d11_trace_register">D3D11_TRACE_REGISTER</a> structure.

<div class="alert"><b>Note</b>  This API requires the Windows Software Development Kit (SDK) for Windows 8.</div>
<div> </div>

## -see-also

<a href="/windows/desktop/direct3d11/d3d11-graphics-reference-shader-enums">Shader Enumerations</a>