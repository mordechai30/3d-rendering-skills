Source: [https://learn.microsoft.com/en-us/windows/win32/api/D3D11/nf-d3d11-id3d11devicecontext-clearstate](<https://learn.microsoft.com/en-us/windows/win32/api/D3D11/nf-d3d11-id3d11devicecontext-clearstate>)

# ID3D11DeviceContext::ClearState


## -description

Restore all default settings.



## -remarks

This method resets any device context to the default settings. This sets all input/output resource slots, shaders, input layouts, predications, scissor rectangles, depth-stencil state, rasterizer state, blend state, sampler state, and viewports to <b>NULL</b>. The primitive topology is set to UNDEFINED.

For a scenario where you would like to clear a list of commands recorded so far, call <a href="/windows/desktop/api/d3d11/nf-d3d11-id3d11devicecontext-finishcommandlist">ID3D11DeviceContext::FinishCommandList</a> and throw away the resulting <a href="/windows/desktop/api/d3d11/nn-d3d11-id3d11commandlist">ID3D11CommandList</a>.

## -see-also

<a href="/windows/desktop/api/d3d11/nn-d3d11-id3d11devicecontext">ID3D11DeviceContext</a>