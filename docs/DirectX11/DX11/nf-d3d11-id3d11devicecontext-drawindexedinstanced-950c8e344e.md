Source: [https://learn.microsoft.com/en-us/windows/win32/api/D3D11/nf-d3d11-id3d11devicecontext-drawindexedinstanced](<https://learn.microsoft.com/en-us/windows/win32/api/D3D11/nf-d3d11-id3d11devicecontext-drawindexedinstanced>)

# ID3D11DeviceContext::DrawIndexedInstanced


## -description

Draw indexed, instanced primitives.

## -parameters

### -param IndexCountPerInstance [in]

Type: <b><a href="/windows/desktop/winprog/windows-data-types">UINT</a></b>

Number of indices read from the index buffer for each instance.

### -param InstanceCount [in]

Type: <b><a href="/windows/desktop/winprog/windows-data-types">UINT</a></b>

Number of instances to draw.

### -param StartIndexLocation [in]

Type: <b><a href="/windows/desktop/winprog/windows-data-types">UINT</a></b>

The location of the first index read by the GPU from the index buffer.

### -param BaseVertexLocation [in]

Type: <b><a href="/windows/desktop/winprog/windows-data-types">INT</a></b>

A value added to each index before reading a vertex from the vertex buffer.

### -param StartInstanceLocation [in]

Type: <b><a href="/windows/desktop/winprog/windows-data-types">UINT</a></b>

A value added to each index before reading per-instance data from a vertex buffer.

## -remarks

A draw API submits work to the rendering pipeline.

Instancing may extend performance by reusing the same geometry to draw multiple objects in a scene. One example of instancing could be to draw the same object with different positions and colors. Instancing requires multiple vertex buffers: at least one for per-vertex data and a second buffer for per-instance data.

The second buffer is needed only if the input layout that you use has elements that use [D3D11_INPUT_PER_INSTANCE_DATA](./ne-d3d11-d3d11_input_classification-3ed464f5be.md) as the input element classification buffer for per-instance data.

## -see-also

<a href="/windows/desktop/api/d3d11/nn-d3d11-id3d11devicecontext">ID3D11DeviceContext</a>