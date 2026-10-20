Source: [https://learn.microsoft.com/en-us/windows/win32/api/D3D11_3/nn-d3d11_3-id3d11unorderedaccessview1](<https://learn.microsoft.com/en-us/windows/win32/api/D3D11_3/nn-d3d11_3-id3d11unorderedaccessview1>)

# ID3D11UnorderedAccessView1 interface


## -description

An unordered-access-view interface represents the parts of a resource the pipeline can access during rendering.

## -inheritance

The <b>ID3D11UnorderedAccessView1</b> interface inherits from <a href="/windows/desktop/api/d3d11/nn-d3d11-id3d11unorderedaccessview">ID3D11UnorderedAccessView</a>. <b>ID3D11UnorderedAccessView1</b> also has these types of members:

## -remarks

To create a view for an unordered access resource, call  <a href="/windows/desktop/api/d3d11_3/nf-d3d11_3-id3d11device3-createunorderedaccessview1">ID3D11Device3::CreateUnorderedAccessView1</a>.

All resources must be bound to the pipeline before they can be accessed. Call <a href="/windows/desktop/api/d3d11/nf-d3d11-id3d11devicecontext-cssetunorderedaccessviews">ID3D11DeviceContext::CSSetUnorderedAccessViews</a> to bind an unordered access view to a compute shader; call <a href="/windows/desktop/api/d3d11/nf-d3d11-id3d11devicecontext-omsetrendertargetsandunorderedaccessviews">ID3D11DeviceContext::OMSetRenderTargetsAndUnorderedAccessViews</a> to bind an unordered access view to a pixel shader.

## -see-also

<a href="/windows/desktop/api/d3d11/nn-d3d11-id3d11unorderedaccessview">ID3D11UnorderedAccessView</a>



<a href="/windows/desktop/direct3d11/d3d11-graphics-reference-resource-interfaces">Resource Interfaces</a>