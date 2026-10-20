Source: [https://learn.microsoft.com/en-us/windows/win32/api/d3d11/nf-d3d11-cd3d11_viewport-cd3d11_viewport(id3d11texture1d_id3d11rendertargetview_float_float_float)](<https://learn.microsoft.com/en-us/windows/win32/api/d3d11/nf-d3d11-cd3d11_viewport-cd3d11_viewport(id3d11texture1d_id3d11rendertargetview_float_float_float)>)

# CD3D11_VIEWPORT::CD3D11_VIEWPORT(ID3D11Texture1D,ID3D11RenderTargetView,FLOAT,FLOAT,FLOAT)


## -description

Instantiates a new instance of a <a href="/previous-versions/windows/desktop/legacy/jj151722(v=vs.85)">CD3D11_VIEWPORT</a> structure that is initialized with **D3D11_TEX1D_RTV** or **D3D11_TEX1D_ARRAY_RTV** values.

## -parameters

### -param pTex1D

A pointer to a **ID3D11Texture1D** interface for a 1D texture.

### -param pRTView

A pointer to a **ID3D11RenderTargetView** interface for the render-target view.

### -param topLeftX

X position of the left hand side of the viewport.
Ranges between **D3D11_VIEWPORT_BOUNDS_MIN** and **D3D11_VIEWPORT_BOUNDS_MAX**.

### -param minDepth

Minimum depth of the viewport.
Ranges between 0 and 1.

### -param maxDepth

Maximum depth of the viewport.
Ranges between 0 and 1.

## -see-also

<a href="/previous-versions/windows/desktop/legacy/jj151722(v=vs.85)">CD3D11_VIEWPORT</a>