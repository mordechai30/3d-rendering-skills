Source: [https://learn.microsoft.com/en-us/windows/win32/api/D3D11/ns-d3d11-d3d11_query_data_so_statistics](<https://learn.microsoft.com/en-us/windows/win32/api/D3D11/ns-d3d11-d3d11_query_data_so_statistics>)

# D3D11_QUERY_DATA_SO_STATISTICS structure


## -description

Query information about the amount of data streamed out to the stream-output buffers in between <a href="/windows/desktop/api/d3d11/nf-d3d11-id3d11devicecontext-begin">ID3D11DeviceContext::Begin</a> and <a href="/windows/desktop/api/d3d11/nf-d3d11-id3d11devicecontext-end">ID3D11DeviceContext::End</a>.

## -struct-fields

### -field NumPrimitivesWritten

Type: <b><a href="/windows/desktop/WinProg/windows-data-types">UINT64</a></b>

Number of primitives (that is, points, lines, and triangles) written to the stream-output buffers.

### -field PrimitivesStorageNeeded

Type: <b><a href="/windows/desktop/WinProg/windows-data-types">UINT64</a></b>

Number of primitives that would have been written to the stream-output buffers if there had been enough space for them all.

## -see-also

<a href="/windows/desktop/direct3d11/d3d11-graphics-reference-d3d11-core-structures">Core Structures</a>