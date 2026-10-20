Source: [https://learn.microsoft.com/en-us/windows/win32/api/D3D11Shader/nf-d3d11shader-id3d11functionlinkinggraph-setoutputsignature](<https://learn.microsoft.com/en-us/windows/win32/api/D3D11Shader/nf-d3d11shader-id3d11functionlinkinggraph-setoutputsignature>)

# ID3D11FunctionLinkingGraph::SetOutputSignature


## -description

Sets the output signature of the function-linking-graph.

## -parameters

### -param pOutputParameters [in]

Type: <b>const <a href="/windows/desktop/api/d3d11shader/ns-d3d11shader-d3d11_parameter_desc">D3D11_PARAMETER_DESC</a>*</b>

An array of  <a href="/windows/desktop/api/d3d11shader/ns-d3d11shader-d3d11_parameter_desc">D3D11_PARAMETER_DESC</a> structures for the parameters of the output signature.

### -param cOutputParameters [in]

Type: <b><a href="/windows/desktop/WinProg/windows-data-types">UINT</a></b>

The number of output parameters in the <i>pOutputParameters</i> array.

### -param ppOutputNode [out]

Type: <b><a href="/windows/desktop/api/d3d11shader/nn-d3d11shader-id3d11linkingnode">ID3D11LinkingNode</a>**</b>

A pointer to a variable that receives a pointer to the <a href="/windows/desktop/api/d3d11shader/nn-d3d11shader-id3d11linkingnode">ID3D11LinkingNode</a> interface that represents the output signature of the function-linking-graph.

## -returns

Type: <b><a href="/windows/win32/com/structure-of-com-error-codes">HRESULT</a></b>

Returns S_OK if successful; otherwise, returns one of the <a href="/windows/desktop/direct3d11/d3d11-graphics-reference-returnvalues">Direct3D 11 Return Codes</a>.

## -see-also

<a href="/windows/desktop/api/d3d11shader/nn-d3d11shader-id3d11functionlinkinggraph">ID3D11FunctionLinkingGraph</a>