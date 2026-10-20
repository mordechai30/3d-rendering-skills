Source: [https://learn.microsoft.com/en-us/windows/win32/api/D3D11/nf-d3d11-id3d11devicecontext-rssetscissorrects](<https://learn.microsoft.com/en-us/windows/win32/api/D3D11/nf-d3d11-id3d11devicecontext-rssetscissorrects>)

# ID3D11DeviceContext::RSSetScissorRects


## -description

Bind an array of scissor rectangles to the rasterizer stage.

## -parameters

### -param NumRects [in]

Type: <b><a href="/windows/desktop/WinProg/windows-data-types">UINT</a></b>

Number of scissor rectangles to bind.

### -param pRects [in, optional]

Type: <b>const <a href="/windows/desktop/direct3d11/d3d11-rect">D3D11_RECT</a>*</b>

An array of scissor rectangles (see <a href="/windows/desktop/direct3d11/d3d11-rect">D3D11_RECT</a>).

## -remarks

All scissor rects must be set atomically as one operation. Any scissor rects not defined by the call are disabled.

The scissor rectangles will only be used if ScissorEnable is set to true in the rasterizer state (see <a href="/windows/desktop/api/d3d11/ns-d3d11-d3d11_rasterizer_desc">D3D11_RASTERIZER_DESC</a>).
        

Which scissor rectangle to use is determined by the SV_ViewportArrayIndex semantic output by a geometry shader (see shader semantic syntax). If a geometry shader does not make use of the SV_ViewportArrayIndex semantic then Direct3D will use the first scissor rectangle in the array.

Each scissor rectangle in the array corresponds to a viewport in an array of viewports (see <a href="/windows/desktop/api/d3d11/nf-d3d11-id3d11devicecontext-rssetviewports">ID3D11DeviceContext::RSSetViewports</a>).
        

<b>Windows Phone 8:
        </b> This API is supported.

## -see-also

<a href="/windows/desktop/api/d3d11/nn-d3d11-id3d11devicecontext">ID3D11DeviceContext</a>