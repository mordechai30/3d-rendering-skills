Source: [https://learn.microsoft.com/en-us/windows/win32/api/d3d11/nf-d3d11-cd3d11_blend_desc-cd3d11_blend_desc(cd3d11_default)](<https://learn.microsoft.com/en-us/windows/win32/api/d3d11/nf-d3d11-cd3d11_blend_desc-cd3d11_blend_desc(cd3d11_default)>)

# CD3D11_BLEND_DESC::CD3D11_BLEND_DESC(CD3D11_DEFAULT)


## -description

Instantiates a new instance of a <a href="/windows/desktop/api/d3d11/ns-d3d11-cd3d11_blend_desc">CD3D11_BLEND_DESC</a> structure that is initialized with default blend-state values.

## -parameters

### -param unnamedParam1

TBD

## -remarks

Here are the default depth-stencil-state values for the members of <a href="/windows/desktop/api/d3d11/ns-d3d11-d3d11_blend_desc">D3D11_BLEND_DESC</a>:


```
AlphaToCoverageEnable = FALSE;
        IndependentBlendEnable = FALSE;
        const D3D11_RENDER_TARGET_BLEND_DESC defaultRenderTargetBlendDesc =
        {
            FALSE,
            D3D11_BLEND_ONE, D3D11_BLEND_ZERO, D3D11_BLEND_OP_ADD,
            D3D11_BLEND_ONE, D3D11_BLEND_ZERO, D3D11_BLEND_OP_ADD,
            D3D11_COLOR_WRITE_ENABLE_ALL,
        };
        for (UINT i = 0; i < D3D11_SIMULTANEOUS_RENDER_TARGET_COUNT; ++i)
            RenderTarget[ i ] = defaultRenderTargetBlendDesc;

```

## -see-also

<a href="/windows/desktop/api/d3d11/ns-d3d11-cd3d11_blend_desc">CD3D11_BLEND_DESC</a>