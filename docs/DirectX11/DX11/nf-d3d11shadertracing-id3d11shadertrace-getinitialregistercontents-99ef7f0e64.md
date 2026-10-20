Source: [https://learn.microsoft.com/en-us/windows/win32/api/D3D11ShaderTracing/nf-d3d11shadertracing-id3d11shadertrace-getinitialregistercontents](<https://learn.microsoft.com/en-us/windows/win32/api/D3D11ShaderTracing/nf-d3d11shadertracing-id3d11shadertrace-getinitialregistercontents>)

# ID3D11ShaderTrace::GetInitialRegisterContents


## -description

Retrieves the initial contents of the specified input register.

## -parameters

### -param pRegister [in]

A pointer to a <a href="/windows/desktop/api/d3d11shadertracing/ns-d3d11shadertracing-d3d11_trace_register">D3D11_TRACE_REGISTER</a> structure that describes the input register to retrieve the initial contents from. You can retrieve valid initial data from only the following input register types. That is, to retrieve valid data, the  <b>RegType</b> member of  <b>D3D11_TRACE_REGISTER</b> must be one of the following values: 

<ul>
<li>D3D11_TRACE_INPUT_REGISTER</li>
<li>D3D11_TRACE_INPUT_PRIMITIVE_ID_REGISTER</li>
<li>D3D11_TRACE_IMMEDIATE_CONSTANT_BUFFER</li>
</ul>
Valid data is indicated by the <b>ValidMask</b> member of the <a href="/windows/desktop/api/d3d11shadertracing/ns-d3d11shadertracing-d3d11_trace_value">D3D11_TRACE_VALUE</a> structure that  <i>pValue</i> points to.

### -param pValue [out]

A pointer to a  <a href="/windows/desktop/api/d3d11shadertracing/ns-d3d11shadertracing-d3d11_trace_value">D3D11_TRACE_VALUE</a> structure. <b>GetInitialRegisterContents</b> fills the members of this structure with information about the initial contents.

## -returns

<b>GetInitialRegisterContents</b> returns:
        <ul>
<li><b>S_OK</b> if the method retrieves the initial register contents.</li>
<li><b>E_FAIL</b> if a trace is not available.</li>
<li><b>E_INVALIDARG</b> if <i>pRegister</i> is invalid or NULL or if <i>pValue</i> is NULL.</li>
<li>Possibly other error codes that are described in <a href="/windows/desktop/direct3d11/d3d11-graphics-reference-returnvalues">Direct3D 11 Return Codes</a>.</li>
</ul>

## -remarks

You can call <b>GetInitialRegisterContents</b> for registers other than the input register types that are specified in the <i>pRegister</i> parameter description. However, <b>GetInitialRegisterContents</b> sets the <b>ValidMask</b> member of the <a href="/windows/desktop/api/d3d11shadertracing/ns-d3d11shadertracing-d3d11_trace_value">D3D11_TRACE_VALUE</a> structure to which  <i>pValue</i> points to empty (all zeros, 0000), and the register values that the <b>Bits</b> member of <b>D3D11_TRACE_VALUE</b> specifies are meaningless. The data that <b>GetInitialRegisterContents</b> returns is not affected by stepping in a trace; however, the data that is returned is affected by changing the stamp index through a call to  <a href="/windows/desktop/api/d3d11shadertracing/nf-d3d11shadertracing-id3d11shadertrace-psselectstamp">ID3D11ShaderTrace::PSSelectStamp</a>.

<div class="alert"><b>Note</b>  This API requires the Windows Software Development Kit (SDK) for Windows 8.</div>
<div> </div>

## -see-also

<a href="/windows/desktop/api/d3d11shadertracing/nn-d3d11shadertracing-id3d11shadertrace">ID3D11ShaderTrace</a>