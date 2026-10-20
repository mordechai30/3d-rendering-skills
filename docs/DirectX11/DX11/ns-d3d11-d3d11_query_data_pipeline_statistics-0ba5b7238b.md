Source: [https://learn.microsoft.com/en-us/windows/win32/api/D3D11/ns-d3d11-d3d11_query_data_pipeline_statistics](<https://learn.microsoft.com/en-us/windows/win32/api/D3D11/ns-d3d11-d3d11_query_data_pipeline_statistics>)

# D3D11_QUERY_DATA_PIPELINE_STATISTICS structure


## -description

Query information about graphics-pipeline activity in between calls to <a href="/windows/desktop/api/d3d11/nf-d3d11-id3d11devicecontext-begin">ID3D11DeviceContext::Begin</a> and <a href="/windows/desktop/api/d3d11/nf-d3d11-id3d11devicecontext-end">ID3D11DeviceContext::End</a>.

## -struct-fields

### -field IAVertices

Type: <b><a href="/windows/desktop/WinProg/windows-data-types">UINT64</a></b>

Number of vertices read by input assembler.

### -field IAPrimitives

Type: <b><a href="/windows/desktop/WinProg/windows-data-types">UINT64</a></b>

Number of primitives read by the input assembler. This number can be different depending on the primitive topology used. For example, a triangle strip with 6 vertices will produce 4 triangles, however a triangle list with 6 vertices will produce 2 triangles.

### -field VSInvocations

Type: <b><a href="/windows/desktop/WinProg/windows-data-types">UINT64</a></b>

Number of times a vertex shader was invoked. Direct3D invokes the vertex shader once per vertex.

### -field GSInvocations

Type: <b><a href="/windows/desktop/WinProg/windows-data-types">UINT64</a></b>

Number of times a geometry shader was invoked. When the geometry shader is set to <b>NULL</b>, this statistic may or may not increment depending on the hardware manufacturer.

### -field GSPrimitives

Type: <b><a href="/windows/desktop/WinProg/windows-data-types">UINT64</a></b>

Number of primitives output by a geometry shader.

### -field CInvocations

Type: <b><a href="/windows/desktop/WinProg/windows-data-types">UINT64</a></b>

Number of primitives that were sent to the rasterizer. When the rasterizer is disabled, this will not increment.

### -field CPrimitives

Type: <b><a href="/windows/desktop/WinProg/windows-data-types">UINT64</a></b>

Number of primitives that were rendered. This may be larger or smaller than CInvocations because after a primitive is clipped sometimes it is either broken up into more than one primitive or completely culled.

### -field PSInvocations

Type: <b><a href="/windows/desktop/WinProg/windows-data-types">UINT64</a></b>

Number of times a pixel shader was invoked.

### -field HSInvocations

Type: <b><a href="/windows/desktop/WinProg/windows-data-types">UINT64</a></b>

Number of times a hull shader was invoked.

### -field DSInvocations

Type: <b><a href="/windows/desktop/WinProg/windows-data-types">UINT64</a></b>

Number of times a domain shader was invoked.

### -field CSInvocations

Type: <b><a href="/windows/desktop/WinProg/windows-data-types">UINT64</a></b>

Number of times a compute shader was invoked.

## -see-also

<a href="/windows/desktop/direct3d11/d3d11-graphics-reference-d3d11-core-structures">Core Structures</a>