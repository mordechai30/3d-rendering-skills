Source: [https://learn.microsoft.com/en-us/windows/win32/api/d3d11/ns-d3d11-d3d11_draw_indexed_instanced_indirect_args](<https://learn.microsoft.com/en-us/windows/win32/api/d3d11/ns-d3d11-d3d11_draw_indexed_instanced_indirect_args>)

# D3D11_DRAW_INDEXED_INSTANCED_INDIRECT_ARGS structure


## -description

Arguments for draw indexed instanced indirect.

## -struct-fields

### -field IndexCountPerInstance

The number of indices read from the index buffer for each instance.

### -field InstanceCount

The number of instances to draw.

### -field StartIndexLocation

The location of the first index read by the GPU from the index buffer.

### -field BaseVertexLocation

A value added to each index before reading a vertex from the vertex buffer.

### -field StartInstanceLocation

A value added to each index before reading per-instance data from a vertex buffer.

## -remarks

The members of this structure serve the same purpose as the parameters of
          <a href="/windows/desktop/api/d3d11/nf-d3d11-id3d11devicecontext-drawindexedinstanced">ID3D11DeviceContext::DrawIndexedInstanced</a>.

## -see-also

<a href="/windows/desktop/direct3d11/d3d11-graphics-reference-d3d11-core-structures">Core Structures</a>