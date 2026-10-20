Source: [https://learn.microsoft.com/en-us/windows/win32/api/D3D11Shader/nf-d3d11shader-id3d11functionlinkinggraph-callfunction](<https://learn.microsoft.com/en-us/windows/win32/api/D3D11Shader/nf-d3d11shader-id3d11functionlinkinggraph-callfunction>)

# ID3D11FunctionLinkingGraph::CallFunction


## -description

Creates a call-function linking node to use in the function-linking-graph.

## -parameters

### -param pModuleInstanceNamespace [in, optional]

Type: <b><a href="/windows/desktop/WinProg/windows-data-types">LPCSTR</a></b>

The optional namespace for the function, or <b>NULL</b> if no namespace is needed.

### -param pModuleWithFunctionPrototype [in]

Type: <b><a href="/windows/desktop/api/d3d11shader/nn-d3d11shader-id3d11module">ID3D11Module</a>*</b>

A pointer to the <a href="/windows/desktop/api/d3d11shader/nn-d3d11shader-id3d11moduleinstance">ID3D11ModuleInstance</a> interface for the library module that contains the function prototype.

### -param pFunctionName [in]

Type: <b><a href="/windows/desktop/WinProg/windows-data-types">LPCSTR</a></b>

The name of the function.

### -param ppCallNode [out]

Type: <b><a href="/windows/desktop/api/d3d11shader/nn-d3d11shader-id3d11linkingnode">ID3D11LinkingNode</a>**</b>

A pointer to a variable that receives a pointer to the <a href="/windows/desktop/api/d3d11shader/nn-d3d11shader-id3d11linkingnode">ID3D11LinkingNode</a> interface that represents the function in the function-linking-graph.

## -returns

Type: <b><a href="/windows/win32/com/structure-of-com-error-codes">HRESULT</a></b>

Returns S_OK if successful; otherwise, returns one of the <a href="/windows/desktop/direct3d11/d3d11-graphics-reference-returnvalues">Direct3D 11 Return Codes</a>.

## -see-also

<a href="/windows/desktop/api/d3d11shader/nn-d3d11shader-id3d11functionlinkinggraph">ID3D11FunctionLinkingGraph</a>