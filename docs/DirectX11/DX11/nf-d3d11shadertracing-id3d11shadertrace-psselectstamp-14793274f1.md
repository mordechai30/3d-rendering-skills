Source: [https://learn.microsoft.com/en-us/windows/win32/api/D3D11ShaderTracing/nf-d3d11shadertracing-id3d11shadertrace-psselectstamp](<https://learn.microsoft.com/en-us/windows/win32/api/D3D11ShaderTracing/nf-d3d11shadertracing-id3d11shadertrace-psselectstamp>)

# ID3D11ShaderTrace::PSSelectStamp


## -description

Sets the specified pixel-shader stamp.

## -parameters

### -param stampIndex [in]

The index of the stamp to select.

## -returns

<b>PSSelectStamp</b> returns:
        <ul>
<li><b>S_OK</b> if the method set the pixel-shader stamp, and if the primitive covers the pixel and sample for the stamp.</li>
<li><b>S_FALSE</b> if the method set the pixel-shader stamp, and if the invocation for the selected stamp falls off the primitive.</li>
<li><b>E_FAIL</b> if you called the method for a vertex shader or geometry shader;   <b>PSSelectStamp</b> is meaningful only for pixel shaders.</li>
<li><b>E_INVALIDARG</b> if <i>stampIndex</i> is out of range [0..3].</li>
<li>Possibly other error codes that are described in <a href="/windows/desktop/direct3d11/d3d11-graphics-reference-returnvalues">Direct3D 11 Return Codes</a>.</li>
</ul>

## -remarks

After you call <b>PSSelectStamp</b> to set the pixel-shader stamp, you can call the <a href="/windows/desktop/api/d3d11shadertracing/nf-d3d11shadertracing-id3d11shadertrace-getinitialregistercontents">ID3D11ShaderTrace::GetInitialRegisterContents</a>,  <a href="/windows/desktop/api/d3d11shadertracing/nf-d3d11shadertracing-id3d11shadertrace-getstep">ID3D11ShaderTrace::GetStep</a>, <a href="/windows/desktop/api/d3d11shadertracing/nf-d3d11shadertracing-id3d11shadertrace-getwrittenregister">ID3D11ShaderTrace::GetWrittenRegister</a>, and <a href="/windows/desktop/api/d3d11shadertracing/nf-d3d11shadertracing-id3d11shadertrace-getreadregister">ID3D11ShaderTrace::GetReadRegister</a> methods to get trace data for that stamp.

<div class="alert"><b>Note</b>  This API requires the Windows Software Development Kit (SDK) for Windows 8.</div>
<div> </div>

## -see-also

<a href="/windows/desktop/api/d3d11shadertracing/nn-d3d11shadertracing-id3d11shadertrace">ID3D11ShaderTrace</a>