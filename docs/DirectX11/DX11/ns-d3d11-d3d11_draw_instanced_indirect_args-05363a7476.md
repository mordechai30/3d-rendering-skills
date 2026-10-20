Source: [https://learn.microsoft.com/en-us/windows/win32/api/d3d11/ns-d3d11-d3d11_draw_instanced_indirect_args](<https://learn.microsoft.com/en-us/windows/win32/api/d3d11/ns-d3d11-d3d11_draw_instanced_indirect_args>)

# D3D11_DRAW_INSTANCED_INDIRECT_ARGS structure


## -description

Arguments for draw instanced indirect.

## -struct-fields

### -field VertexCountPerInstance

The number of vertices to draw.

### -field InstanceCount

The number of instances to draw.

### -field StartVertexLocation

The index of the first vertex.

### -field StartInstanceLocation

A value added to each index before reading per-instance data from a vertex buffer.

## -remarks

The members of this structure serve the same purpose as the parameters of
          <a href="/windows/desktop/api/d3d11/nf-d3d11-id3d11devicecontext-drawinstanced">ID3D11DeviceContext::DrawInstanced</a>.

## -see-also

<a href="/windows/desktop/direct3d11/d3d11-graphics-reference-d3d11-core-structures">Core Structures</a>