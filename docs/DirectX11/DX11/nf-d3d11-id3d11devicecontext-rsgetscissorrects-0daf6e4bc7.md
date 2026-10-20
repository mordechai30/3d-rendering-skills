Source: [https://learn.microsoft.com/en-us/windows/win32/api/D3D11/nf-d3d11-id3d11devicecontext-rsgetscissorrects](<https://learn.microsoft.com/en-us/windows/win32/api/D3D11/nf-d3d11-id3d11devicecontext-rsgetscissorrects>)

# ID3D11DeviceContext::RSGetScissorRects


## -description

Get the array of scissor rectangles bound to the rasterizer stage.

## -parameters

### -param pNumRects [in, out]

Type: <b><a href="/windows/desktop/WinProg/windows-data-types">UINT</a>*</b>

The number of scissor rectangles (ranges between 0 and D3D11_VIEWPORT_AND_SCISSORRECT_OBJECT_COUNT_PER_PIPELINE) bound; set <i>pRects</i> to <b>NULL</b> to use <i>pNumRects</i> to see how many rectangles would be returned.

### -param pRects [out, optional]

Type: <b><a href="/windows/desktop/direct3d11/d3d11-rect">D3D11_RECT</a>*</b>

An array of scissor rectangles (see <a href="/windows/desktop/direct3d11/d3d11-rect">D3D11_RECT</a>). If NumRects is greater than the number of scissor rects currently bound, then unused members of the array will contain 0.

## -see-also

<a href="/windows/desktop/api/d3d11/nn-d3d11-id3d11devicecontext">ID3D11DeviceContext</a>