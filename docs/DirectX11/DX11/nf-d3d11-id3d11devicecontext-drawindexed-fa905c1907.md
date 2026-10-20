Source: [https://learn.microsoft.com/en-us/windows/win32/api/D3D11/nf-d3d11-id3d11devicecontext-drawindexed](<https://learn.microsoft.com/en-us/windows/win32/api/D3D11/nf-d3d11-id3d11devicecontext-drawindexed>)

# ID3D11DeviceContext::DrawIndexed


## -description

Draw indexed, non-instanced primitives.

## -parameters

### -param IndexCount [in]

Type: <b><a href="/windows/desktop/WinProg/windows-data-types">UINT</a></b>

Number of indices to draw.

### -param StartIndexLocation [in]

Type: <b><a href="/windows/desktop/WinProg/windows-data-types">UINT</a></b>

The location of the first index read by the GPU from the index buffer.

### -param BaseVertexLocation [in]

Type: <b><a href="/windows/desktop/WinProg/windows-data-types">INT</a></b>

A value added to each index before reading a vertex from the vertex buffer.

## -remarks

A draw API submits work to the rendering pipeline.

If the sum of both indices is negative, the result of the function call is undefined.

## -see-also

<a href="/windows/desktop/api/d3d11/nn-d3d11-id3d11devicecontext">ID3D11DeviceContext</a>