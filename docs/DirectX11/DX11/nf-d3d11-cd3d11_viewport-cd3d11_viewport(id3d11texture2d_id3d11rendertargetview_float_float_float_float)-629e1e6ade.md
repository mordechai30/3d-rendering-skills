Source: [https://learn.microsoft.com/en-us/windows/win32/api/d3d11/nf-d3d11-cd3d11_viewport-cd3d11_viewport(id3d11texture2d_id3d11rendertargetview_float_float_float_float)](<https://learn.microsoft.com/en-us/windows/win32/api/d3d11/nf-d3d11-cd3d11_viewport-cd3d11_viewport(id3d11texture2d_id3d11rendertargetview_float_float_float_float)>)

# CD3D11_VIEWPORT::CD3D11_VIEWPORT(ID3D11Texture2D,ID3D11RenderTargetView,FLOAT,FLOAT,FLOAT,FLOAT)


## -description

Instantiates a new instance of a <a href="/previous-versions/windows/desktop/legacy/jj151722(v=vs.85)">CD3D11_VIEWPORT</a> structure that is initialized with 2D texture values.

## -parameters

### -param pTex2D

A pointer to a **ID3D11Texture2D** interface for a 2D texture.

### -param pRTView

A pointer to a **ID3D11RenderTargetView** interface for the render-target view.

### -param topLeftX

X position of the left hand side of the viewport.
Ranges between **D3D11_VIEWPORT_BOUNDS_MIN** and **D3D11_VIEWPORT_BOUNDS_MAX**.

### -param topLeftY

Y position of the top of the viewport.
Ranges between **D3D11_VIEWPORT_BOUNDS_MIN** and **D3D11_VIEWPORT_BOUNDS_MAX**.

### -param minDepth

Minimum depth of the viewport.
Ranges between 0 and 1.

### -param maxDepth

Maximum depth of the viewport.
Ranges between 0 and 1.

## -see-also

<a href="/previous-versions/windows/desktop/legacy/jj151722(v=vs.85)">CD3D11_VIEWPORT</a>