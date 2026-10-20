Source: [https://learn.microsoft.com/en-us/windows/win32/api/d3d11/nn-d3d11-id3d11predicate](<https://learn.microsoft.com/en-us/windows/win32/api/d3d11/nn-d3d11-id3d11predicate>)

# ID3D11Predicate interface


## -description

A predicate interface determines whether geometry should be processed depending on the results of a previous draw call.

## -remarks

To create a predicate object, call <a href="/windows/desktop/api/d3d11/nf-d3d11-id3d11device-createpredicate">ID3D11Device::CreatePredicate</a>. To set the predicate object, call <a href="/windows/desktop/api/d3d11/nf-d3d11-id3d11devicecontext-setpredication">ID3D11DeviceContext::SetPredication</a>.

There are two types of predicates: stream-output-overflow predicates and occlusion predicates. Stream-output-overflow predicates cause any geometry residing in stream-output buffers that were overflowed to not be processed. Occlusion predicates cause any geometry that did not have a single sample pass the depth/stencil tests to not be processed.

## -see-also

<a href="/windows/desktop/direct3d11/d3d11-graphics-reference-d3d11-core-interfaces">Core Interfaces</a>



<a href="/windows/desktop/api/d3d11/nn-d3d11-id3d11query">ID3D11Query</a>