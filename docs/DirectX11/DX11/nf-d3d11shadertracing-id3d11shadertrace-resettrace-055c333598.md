Source: [https://learn.microsoft.com/en-us/windows/win32/api/D3D11ShaderTracing/nf-d3d11shadertracing-id3d11shadertrace-resettrace](<https://learn.microsoft.com/en-us/windows/win32/api/D3D11ShaderTracing/nf-d3d11shadertracing-id3d11shadertrace-resettrace>)

# ID3D11ShaderTrace::ResetTrace


## -description

Resets the shader-trace object.



## -remarks

After you call <b>ResetTrace</b>, the <a href="/windows/desktop/api/d3d11shadertracing/nn-d3d11shadertracing-id3d11shadertrace">ID3D11ShaderTrace</a> object behaves as if it had just been created. Thereafter, shader invocations for the trace start from 0 again; calls to <a href="/windows/desktop/api/d3d11shadertracing/nf-d3d11shadertracing-id3d11shadertrace-traceready">ID3D11ShaderTrace::TraceReady</a> return <b>S_FALSE</b> until the selected shader invocation number is reached, and <b>TraceReady</b> records a new trace.

<div class="alert"><b>Note</b>  This API requires the Windows Software Development Kit (SDK) for Windows 8.</div>
<div> </div>

## -see-also

<a href="/windows/desktop/api/d3d11shadertracing/nn-d3d11shadertracing-id3d11shadertrace">ID3D11ShaderTrace</a>