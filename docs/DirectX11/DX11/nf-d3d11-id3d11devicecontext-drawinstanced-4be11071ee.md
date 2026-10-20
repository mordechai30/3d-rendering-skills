Source: [https://learn.microsoft.com/en-us/windows/win32/api/D3D11/nf-d3d11-id3d11devicecontext-drawinstanced](<https://learn.microsoft.com/en-us/windows/win32/api/D3D11/nf-d3d11-id3d11devicecontext-drawinstanced>)

# ID3D11DeviceContext::DrawInstanced


## -description

Draw non-indexed, instanced primitives.

## -parameters

### -param VertexCountPerInstance [in]

Type: <b><a href="/windows/desktop/WinProg/windows-data-types">UINT</a></b>

Number of vertices to draw.

### -param InstanceCount [in]

Type: <b><a href="/windows/desktop/WinProg/windows-data-types">UINT</a></b>

Number of instances to draw.

### -param StartVertexLocation [in]

Type: <b><a href="/windows/desktop/WinProg/windows-data-types">UINT</a></b>

Index of the first vertex.

### -param StartInstanceLocation [in]

Type: <b><a href="/windows/desktop/WinProg/windows-data-types">UINT</a></b>

A value added to each index before reading per-instance data from a vertex buffer.

## -remarks

A draw API submits work to the rendering pipeline.

Instancing may extend performance by reusing the same geometry to draw multiple objects in a scene. One example of instancing could be 
      to draw the same object with different positions and colors.

The vertex data for an instanced draw call normally comes from a vertex buffer that is bound to the pipeline. 
      However, you could also provide the vertex data from a shader that has instanced data identified with a system-value semantic (SV_InstanceID).

## -see-also

<a href="/windows/desktop/api/d3d11/nn-d3d11-id3d11devicecontext">ID3D11DeviceContext</a>