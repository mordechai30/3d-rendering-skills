Source: [https://learn.microsoft.com/en-us/windows/win32/api/D3D11ShaderTracing/nf-d3d11shadertracing-id3d11shadertrace-gettracestats](<https://learn.microsoft.com/en-us/windows/win32/api/D3D11ShaderTracing/nf-d3d11shadertracing-id3d11shadertrace-gettracestats>)

# ID3D11ShaderTrace::GetTraceStats


## -description

Returns statistics about the trace.

## -parameters

### -param pTraceStats [out]

A pointer to a <a href="/windows/desktop/api/d3d11shadertracing/ns-d3d11shadertracing-d3d11_trace_stats">D3D11_TRACE_STATS</a> structure. <b>GetTraceStats</b> fills the members of this structure with statistics about the trace.

## -returns

<b>GetTraceStats</b> returns:
        <ul>
<li>S_OK if statistics about the trace are successfully obtained.</li>
<li>E_FAIL if no trace statistics are available yet; <a href="/windows/desktop/api/d3d11shadertracing/nf-d3d11shadertracing-id3d11shadertrace-traceready">ID3D11ShaderTrace::TraceReady</a> must return S_OK before <b>GetTraceStats</b> can succeed.</li>
<li>E_INVALIDARG if <i>pTraceStats</i> is NULL.</li>
<li>Possibly other error codes that are described in <a href="/windows/desktop/direct3d11/d3d11-graphics-reference-returnvalues">Direct3D 11 Return Codes</a>.</li>
</ul>

## -remarks

This API requires the Windows Software Development Kit (SDK) for Windows 8.

## -see-also

<a href="/windows/desktop/api/d3d11shadertracing/nn-d3d11shadertracing-id3d11shadertrace">ID3D11ShaderTrace</a>