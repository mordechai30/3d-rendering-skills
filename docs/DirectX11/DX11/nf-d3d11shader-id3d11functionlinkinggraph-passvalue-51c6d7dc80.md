Source: [https://learn.microsoft.com/en-us/windows/win32/api/D3D11Shader/nf-d3d11shader-id3d11functionlinkinggraph-passvalue](<https://learn.microsoft.com/en-us/windows/win32/api/D3D11Shader/nf-d3d11shader-id3d11functionlinkinggraph-passvalue>)

# ID3D11FunctionLinkingGraph::PassValue


## -description

Passes a value from a source linking node to a destination linking node.

## -parameters

### -param pSrcNode [in]

Type: <b><a href="/windows/desktop/api/d3d11shader/nn-d3d11shader-id3d11linkingnode">ID3D11LinkingNode</a>*</b>

A pointer to the <a href="/windows/desktop/api/d3d11shader/nn-d3d11shader-id3d11linkingnode">ID3D11LinkingNode</a> interface for the source linking node.

### -param SrcParameterIndex [in]

Type: <b>INT</b>

The zero-based index of the source parameter.

### -param pDstNode [in]

Type: <b><a href="/windows/desktop/api/d3d11shader/nn-d3d11shader-id3d11linkingnode">ID3D11LinkingNode</a>*</b>

A pointer to the <a href="/windows/desktop/api/d3d11shader/nn-d3d11shader-id3d11linkingnode">ID3D11LinkingNode</a> interface for the destination linking node.

### -param DstParameterIndex [in]

Type: <b>INT</b>

The zero-based index of the destination parameter.

## -returns

Type: <b><a href="/windows/win32/com/structure-of-com-error-codes">HRESULT</a></b>

Returns S_OK if successful; otherwise, returns one of the <a href="/windows/desktop/direct3d11/d3d11-graphics-reference-returnvalues">Direct3D 11 Return Codes</a>.

## -see-also

<a href="/windows/desktop/api/d3d11shader/nn-d3d11shader-id3d11functionlinkinggraph">ID3D11FunctionLinkingGraph</a>