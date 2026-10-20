Source: [https://learn.microsoft.com/en-us/windows/win32/api/D3D11Shader/nf-d3d11shader-id3d11functionlinkinggraph-generatehlsl](<https://learn.microsoft.com/en-us/windows/win32/api/D3D11Shader/nf-d3d11shader-id3d11functionlinkinggraph-generatehlsl>)

# ID3D11FunctionLinkingGraph::GenerateHlsl


## -description

Generates Microsoft High Level Shader Language (HLSL) shader code that represents the function-linking-graph.

## -parameters

### -param uFlags [in]

Type: <b><a href="/windows/desktop/WinProg/windows-data-types">UINT</a></b>

Reserved

### -param ppBuffer [out]

Type: <b><a href="/previous-versions/windows/desktop/legacy/ff728743(v=vs.85)">ID3DBlob</a>**</b>

An pointer to a variable that receives a pointer to the <a href="/previous-versions/windows/desktop/legacy/ff728743(v=vs.85)">ID3DBlob</a> interface that you can use to access the HLSL shader source code that represents the function-linking-graph. You can compile this HLSL code, but first you must  add code or include statements for the functions called in the function-linking-graph.

## -returns

Type: <b><a href="/windows/win32/com/structure-of-com-error-codes">HRESULT</a></b>

Returns S_OK if successful; otherwise, returns one of the <a href="/windows/desktop/direct3d11/d3d11-graphics-reference-returnvalues">Direct3D 11 Return Codes</a>.

## -see-also

<a href="/windows/desktop/api/d3d11shader/nn-d3d11shader-id3d11functionlinkinggraph">ID3D11FunctionLinkingGraph</a>