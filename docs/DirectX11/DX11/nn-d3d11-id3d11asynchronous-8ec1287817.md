Source: [https://learn.microsoft.com/en-us/windows/win32/api/D3D11/nn-d3d11-id3d11asynchronous](<https://learn.microsoft.com/en-us/windows/win32/api/D3D11/nn-d3d11-id3d11asynchronous>)

# ID3D11Asynchronous interface


## -description

This interface encapsulates methods for retrieving data from the GPU asynchronously.

## -inheritance

The <b>ID3D11Asynchronous</b> interface inherits from <a href="/windows/desktop/api/d3d11/nn-d3d11-id3d11devicechild">ID3D11DeviceChild</a>. <b>ID3D11Asynchronous</b> also has these types of members:

## -remarks

There are three types of asynchronous interfaces, all of which inherit this interface:

<ul>
<li>
<a href="/windows/desktop/api/d3d11/nn-d3d11-id3d11query">ID3D11Query</a> - Queries information from the GPU.</li>
<li>
<a href="/windows/desktop/api/d3d11/nn-d3d11-id3d11predicate">ID3D11Predicate</a> - Determines whether a piece of geometry should be processed or not depending on the results of a previous draw call.</li>
<li>
<a href="/windows/desktop/api/d3d11/nn-d3d11-id3d11counter">ID3D11Counter</a> - Measures GPU performance.</li>
</ul>

## -see-also

<a href="/windows/desktop/direct3d11/d3d11-graphics-reference-d3d11-core-interfaces">Core Interfaces</a>



<a href="/windows/desktop/api/d3d11/nn-d3d11-id3d11devicechild">ID3D11DeviceChild</a>