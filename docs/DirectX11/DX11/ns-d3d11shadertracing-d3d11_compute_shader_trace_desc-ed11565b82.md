Source: [https://learn.microsoft.com/en-us/windows/win32/api/D3D11ShaderTracing/ns-d3d11shadertracing-d3d11_compute_shader_trace_desc](<https://learn.microsoft.com/en-us/windows/win32/api/D3D11ShaderTracing/ns-d3d11shadertracing-d3d11_compute_shader_trace_desc>)

# D3D11_COMPUTE_SHADER_TRACE_DESC structure


## -description

Describes an instance of a compute shader to trace.

## -struct-fields

### -field Invocation

The invocation number of the instance of the compute shader.

### -field ThreadIDInGroup

The <a href="/windows/desktop/direct3dhlsl/sv-groupthreadid">SV_GroupThreadID</a> to trace. This value identifies indexes of individual threads within a thread group that a compute shader executes in.

### -field ThreadGroupID

The <a href="/windows/desktop/direct3dhlsl/sv-groupid">SV_GroupID</a> to trace. This value identifies indexes of a thread group that the compute shader executes in.

## -remarks

This API requires the Windows Software Development Kit (SDK) for Windows 8.

## -see-also

<a href="/windows/desktop/direct3d11/d3d11-graphics-reference-shader-structures">Shader Structures</a>