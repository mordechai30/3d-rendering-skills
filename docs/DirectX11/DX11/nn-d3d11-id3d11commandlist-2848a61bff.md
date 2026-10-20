Source: [https://learn.microsoft.com/en-us/windows/win32/api/D3D11/nn-d3d11-id3d11commandlist](<https://learn.microsoft.com/en-us/windows/win32/api/D3D11/nn-d3d11-id3d11commandlist>)

# ID3D11CommandList interface


## -description

The <b>ID3D11CommandList</b> interface encapsulates a list of graphics commands for play back.

## -inheritance

The <b>ID3D11CommandList</b> interface inherits from <a href="/windows/desktop/api/d3d11/nn-d3d11-id3d11devicechild">ID3D11DeviceChild</a>. <b>ID3D11CommandList</b> also has these types of members:

## -remarks

There is no explicit creation method, simply declare an <b>ID3D11CommandList</b> interface, then call <a href="/windows/desktop/api/d3d11/nf-d3d11-id3d11devicecontext-finishcommandlist">ID3D11DeviceContext::FinishCommandList</a> to record commands or <a href="/windows/desktop/api/d3d11/nf-d3d11-id3d11devicecontext-executecommandlist">ID3D11DeviceContext::ExecuteCommandList</a> to play back commands.

## -see-also

<a href="/windows/desktop/direct3d11/d3d11-graphics-reference-d3d11-core-interfaces">Core Interfaces</a>



<a href="/windows/desktop/api/d3d11/nn-d3d11-id3d11devicechild">ID3D11DeviceChild</a>