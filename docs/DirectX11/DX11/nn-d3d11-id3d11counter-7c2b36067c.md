Source: [https://learn.microsoft.com/en-us/windows/win32/api/D3D11/nn-d3d11-id3d11counter](<https://learn.microsoft.com/en-us/windows/win32/api/D3D11/nn-d3d11-id3d11counter>)

# ID3D11Counter interface


## -description

This interface encapsulates methods for measuring GPU performance.

## -inheritance

The <b>ID3D11Counter</b> interface inherits from <a href="/windows/desktop/api/d3d11/nn-d3d11-id3d11asynchronous">ID3D11Asynchronous</a>. <b>ID3D11Counter</b> also has these types of members:

## -remarks

A counter can be created with <a href="/windows/desktop/api/d3d11/nf-d3d11-id3d11device-createcounter">ID3D11Device::CreateCounter</a>.

This is a derived class of <a href="/windows/desktop/api/d3d11/nn-d3d11-id3d11asynchronous">ID3D11Asynchronous</a>.

Counter data is gathered by issuing an <a href="/windows/desktop/api/d3d11/nf-d3d11-id3d11devicecontext-begin">ID3D11DeviceContext::Begin</a> command, issuing some graphics commands, issuing an <a href="/windows/desktop/api/d3d11/nf-d3d11-id3d11devicecontext-end">ID3D11DeviceContext::End</a> command, and then calling <a href="/windows/desktop/api/d3d11/nf-d3d11-id3d11devicecontext-getdata">ID3D11DeviceContext::GetData</a> to get data about what happened in between the Begin and End calls. The data returned by GetData will be different depending on the type of counter. The call to End causes the data returned by GetData to be accurate up until the last call to End.

Counters are best suited for profiling.

For a list of the types of performance counters, see <a href="/windows/desktop/api/d3d11/ne-d3d11-d3d11_counter">D3D11_COUNTER</a>.

## -see-also

<a href="/windows/desktop/direct3d11/d3d11-graphics-reference-d3d11-core-interfaces">Core Interfaces</a>



<a href="/windows/desktop/api/d3d11/nn-d3d11-id3d11asynchronous">ID3D11Asynchronous</a>