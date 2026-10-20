Source: [https://learn.microsoft.com/en-us/windows/win32/api/D3D11_3/nn-d3d11_3-id3d11query1](<https://learn.microsoft.com/en-us/windows/win32/api/D3D11_3/nn-d3d11_3-id3d11query1>)

# ID3D11Query1 interface


## -description

Represents a query object for querying information from the graphics processing unit (GPU).

## -inheritance

The <b>ID3D11Query1</b> interface inherits from <a href="/windows/desktop/api/d3d11/nn-d3d11-id3d11query">ID3D11Query</a>. <b>ID3D11Query1</b> also has these types of members:

## -remarks

A query can be created with <a href="/windows/desktop/api/d3d11_3/nf-d3d11_3-id3d11device3-createquery1">ID3D11Device3::CreateQuery1</a>.

Query data is typically gathered by issuing an <a href="/windows/desktop/api/d3d11/nf-d3d11-id3d11devicecontext-begin">ID3D11DeviceContext::Begin</a> command, issuing some graphics commands, issuing an <a href="/windows/desktop/api/d3d11/nf-d3d11-id3d11devicecontext-end">ID3D11DeviceContext::End</a> command, and then calling <a href="/windows/desktop/api/d3d11/nf-d3d11-id3d11devicecontext-getdata">ID3D11DeviceContext::GetData</a> to get data about what happened in between the Begin and End calls. The data returned by <b>GetData</b> will be different depending on the type of query.

There are, however, some queries that do not require calls to <a href="/windows/desktop/api/d3d11/nf-d3d11-id3d11devicecontext-begin">Begin</a>. For a list of possible queries see <a href="/windows/desktop/api/d3d11/ne-d3d11-d3d11_query">D3D11_QUERY</a>.

When using a query that does not require a call to <a href="/windows/desktop/api/d3d11/nf-d3d11-id3d11devicecontext-begin">Begin</a>, it still requires a call to <a href="/windows/desktop/api/d3d11/nf-d3d11-id3d11devicecontext-end">End</a>. The call to <b>End</b> causes the data returned by <a href="/windows/desktop/api/d3d11/nf-d3d11-id3d11devicecontext-getdata">GetData</a> to be accurate up until the last call to <b>End</b>.

## -see-also

<a href="/windows/desktop/direct3d11/d3d11-graphics-reference-d3d11-core-interfaces">Core Interfaces</a>



<a href="/windows/desktop/api/d3d11/nn-d3d11-id3d11query">ID3D11Query</a>