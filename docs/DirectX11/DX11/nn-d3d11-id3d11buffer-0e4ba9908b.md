Source: [https://learn.microsoft.com/en-us/windows/win32/api/D3D11/nn-d3d11-id3d11buffer](<https://learn.microsoft.com/en-us/windows/win32/api/D3D11/nn-d3d11-id3d11buffer>)

# ID3D11Buffer interface


## -description

A buffer interface accesses a buffer resource, which is unstructured memory. Buffers typically store vertex or index data.

## -inheritance

The <b>ID3D11Buffer</b> interface inherits from <a href="/windows/desktop/api/d3d11/nn-d3d11-id3d11resource">ID3D11Resource</a>. <b>ID3D11Buffer</b> also has these types of members:

## -remarks

There are three types of buffers: vertex, index, or a shader-constant buffer. Create a buffer resource by calling <a href="/windows/desktop/api/d3d11/nf-d3d11-id3d11device-createbuffer">ID3D11Device::CreateBuffer</a>.

A buffer must be bound to the pipeline before it can be accessed. Buffers can be bound to the input-assembler stage by calls to <a href="/windows/desktop/api/d3d11/nf-d3d11-id3d11devicecontext-iasetvertexbuffers">ID3D11DeviceContext::IASetVertexBuffers</a> and <a href="/windows/desktop/api/d3d11/nf-d3d11-id3d11devicecontext-iasetindexbuffer">ID3D11DeviceContext::IASetIndexBuffer</a>, to the stream-output stage by a call to <a href="/windows/desktop/api/d3d11/nf-d3d11-id3d11devicecontext-sosettargets">ID3D11DeviceContext::SOSetTargets</a>, and to a shader stage by calling the appropriate shader method (such as <a href="/windows/desktop/api/d3d11/nf-d3d11-id3d11devicecontext-vssetconstantbuffers">ID3D11DeviceContext::VSSetConstantBuffers</a> for example).

Buffers can be bound to multiple pipeline stages simultaneously for reading. A buffer can also be bound to a single pipeline stage for writing; however, the same buffer cannot be bound for reading and writing simultaneously.

## -see-also

<a href="/windows/desktop/api/d3d11/nn-d3d11-id3d11resource">ID3D11Resource</a>



<a href="/windows/desktop/direct3d11/d3d11-graphics-reference-resource-interfaces">Resource Interfaces</a>