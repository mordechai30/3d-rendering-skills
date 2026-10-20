Source: [https://learn.microsoft.com/en-us/windows/win32/api/D3D11/ns-d3d11-d3d11_query_data_timestamp_disjoint](<https://learn.microsoft.com/en-us/windows/win32/api/D3D11/ns-d3d11-d3d11_query_data_timestamp_disjoint>)

# D3D11_QUERY_DATA_TIMESTAMP_DISJOINT structure


## -description

Query information about the reliability of a timestamp query.

## -struct-fields

### -field Frequency

Type: <b><a href="/windows/desktop/WinProg/windows-data-types">UINT64</a></b>

How frequently the GPU counter increments in Hz.

### -field Disjoint

Type: <b><a href="/windows/desktop/WinProg/windows-data-types">BOOL</a></b>

If this is <b>TRUE</b>, something occurred in between the query's <a href="/windows/desktop/api/d3d11/nf-d3d11-id3d11devicecontext-begin">ID3D11DeviceContext::Begin</a> and <a href="/windows/desktop/api/d3d11/nf-d3d11-id3d11devicecontext-end">ID3D11DeviceContext::End</a> calls that caused the timestamp counter to become discontinuous or disjoint, such as unplugging the AC cord on a laptop, overheating, or throttling up/down due to laptop savings events. The timestamp returned by <a href="/windows/desktop/api/d3d11/nf-d3d11-id3d11devicecontext-getdata">ID3D11DeviceContext::GetData</a> for a timestamp query is only reliable if <b>Disjoint</b> is <b>FALSE</b>.

## -remarks

For a list of query types see <a href="/windows/desktop/api/d3d11/ne-d3d11-d3d11_query">D3D11_QUERY</a>.

## -see-also

<a href="/windows/desktop/direct3d11/d3d11-graphics-reference-d3d11-core-structures">Core Structures</a>