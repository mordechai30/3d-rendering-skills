Source: [https://learn.microsoft.com/en-us/windows/win32/api/D3D11ShaderTracing/nf-d3d11shadertracing-id3d11shadertrace-getwrittenregister](<https://learn.microsoft.com/en-us/windows/win32/api/D3D11ShaderTracing/nf-d3d11shadertracing-id3d11shadertrace-getwrittenregister>)

# ID3D11ShaderTrace::GetWrittenRegister


## -description

Retrieves information about a register that was written by a step in the trace.

## -parameters

### -param stepIndex [in]

The index of the step within the trace. The range of the index is [0...NumTraceSteps-1], where <b>NumTraceSteps</b> is a member of the  <a href="/windows/desktop/api/d3d11shadertracing/ns-d3d11shadertracing-d3d11_trace_stats">D3D11_TRACE_STATS</a> structure. You can retrieve information in any step order.

### -param writtenRegisterIndex [in]

The index of the register within  the trace step. The range of the index is [0...NumRegistersWritten-1], where <b>NumRegistersWritten</b> is a member of the  <a href="/windows/desktop/api/d3d11shadertracing/ns-d3d11shadertracing-d3d11_trace_step">D3D11_TRACE_STEP</a> structure.

### -param pRegister [out]

A pointer to a <a href="/windows/desktop/api/d3d11shadertracing/ns-d3d11shadertracing-d3d11_trace_register">D3D11_TRACE_REGISTER</a> structure. <b>GetWrittenRegister</b> fills the members of this structure with information about the register that was written by the step in the trace.

### -param pValue [out]

A pointer to a  <a href="/windows/desktop/api/d3d11shadertracing/ns-d3d11shadertracing-d3d11_trace_value">D3D11_TRACE_VALUE</a> structure. <b>GetWrittenRegister</b> fills the members of this structure with information about the value that was written to the register.

## -returns

<b>GetWrittenRegister</b> returns:
        <ul>
<li><b>S_OK</b> if the method retrieves the register information.</li>
<li><b>E_FAIL</b> if a trace is not available or if the trace was not created with the D3D11_SHADER_TRACE_FLAG_RECORD_REGISTER_WRITES flag.</li>
<li><b>E_INVALIDARG</b> if <i>stepIndex</i> or <i>writtenRegisterIndex</i> is out of range or if <i>pRegister</i> or <i>pValue</i> is NULL.</li>
<li>Possibly other error codes that are described in <a href="/windows/desktop/direct3d11/d3d11-graphics-reference-returnvalues">Direct3D 11 Return Codes</a>.</li>
</ul>

## -remarks

This API requires the Windows Software Development Kit (SDK) for Windows 8.

## -see-also

<a href="/windows/desktop/api/d3d11shadertracing/nn-d3d11shadertracing-id3d11shadertrace">ID3D11ShaderTrace</a>