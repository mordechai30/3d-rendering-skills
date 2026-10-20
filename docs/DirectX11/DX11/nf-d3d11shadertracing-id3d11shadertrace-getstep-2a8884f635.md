Source: [https://learn.microsoft.com/en-us/windows/win32/api/D3D11ShaderTracing/nf-d3d11shadertracing-id3d11shadertrace-getstep](<https://learn.microsoft.com/en-us/windows/win32/api/D3D11ShaderTracing/nf-d3d11shadertracing-id3d11shadertrace-getstep>)

# ID3D11ShaderTrace::GetStep


## -description

Retrieves information about the specified step in the trace.

## -parameters

### -param stepIndex [in]

The index of the step within the trace. The range of the index is [0...NumTraceSteps-1], where <b>NumTraceSteps</b> is a member of the  <a href="/windows/desktop/api/d3d11shadertracing/ns-d3d11shadertracing-d3d11_trace_stats">D3D11_TRACE_STATS</a> structure. You can retrieve information about a step in any step order.

### -param pTraceStep [out]

A pointer to a  <a href="/windows/desktop/api/d3d11shadertracing/ns-d3d11shadertracing-d3d11_trace_step">D3D11_TRACE_STEP</a> structure. <b>GetStep</b> fills the members of this structure with information about the trace step that is specified by the <i>stepIndex</i>  parameter.

## -returns

<b>GetStep</b> returns:
        <ul>
<li><b>S_OK</b> if the method retrieves the step information.</li>
<li><b>E_FAIL</b> if a trace is not available.</li>
<li><b>E_INVALIDARG</b> if <i>stepIndex</i> is out of range or if <i>pTraceStep</i> is NULL.</li>
<li>Possibly other error codes that are described in <a href="/windows/desktop/direct3d11/d3d11-graphics-reference-returnvalues">Direct3D 11 Return Codes</a>.</li>
</ul>

## -remarks

This API requires the Windows Software Development Kit (SDK) for Windows 8.

## -see-also

<a href="/windows/desktop/api/d3d11shadertracing/nn-d3d11shadertracing-id3d11shadertrace">ID3D11ShaderTrace</a>