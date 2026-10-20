Source: [https://learn.microsoft.com/en-us/windows/win32/api/D3D11/nf-d3d11-id3d11devicecontext-draw](<https://learn.microsoft.com/en-us/windows/win32/api/D3D11/nf-d3d11-id3d11devicecontext-draw>)

# ID3D11DeviceContext::Draw


## -description

Draw non-indexed, non-instanced primitives.

## -parameters

### -param VertexCount [in]

Type: <b><a href="/windows/desktop/WinProg/windows-data-types">UINT</a></b>

Number of vertices to draw.

### -param StartVertexLocation [in]

Type: <b><a href="/windows/desktop/WinProg/windows-data-types">UINT</a></b>

Index of the first vertex, which is usually an offset in a vertex buffer.

## -remarks

<b>Draw</b> submits work to the rendering pipeline.

The vertex data for a draw call normally comes from a vertex buffer that is bound to the pipeline.

Even without any vertex buffer bound to the pipeline, you can generate your own vertex data in your vertex shader by using the <a href="/windows/desktop/direct3dhlsl/dx-graphics-hlsl-semantics">SV_VertexID</a> system-value semantic to determine the current vertex that the runtime is processing.

## -see-also

<a href="/windows/desktop/api/d3d11/nn-d3d11-id3d11devicecontext">ID3D11DeviceContext</a>