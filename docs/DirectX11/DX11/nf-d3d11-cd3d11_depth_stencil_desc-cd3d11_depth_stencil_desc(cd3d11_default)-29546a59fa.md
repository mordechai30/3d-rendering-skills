Source: [https://learn.microsoft.com/en-us/windows/win32/api/d3d11/nf-d3d11-cd3d11_depth_stencil_desc-cd3d11_depth_stencil_desc(cd3d11_default)](<https://learn.microsoft.com/en-us/windows/win32/api/d3d11/nf-d3d11-cd3d11_depth_stencil_desc-cd3d11_depth_stencil_desc(cd3d11_default)>)

# CD3D11_DEPTH_STENCIL_DESC::CD3D11_DEPTH_STENCIL_DESC(CD3D11_DEFAULT)


## -description

Instantiates a new instance of a <a href="/previous-versions/windows/desktop/legacy/jj151632(v=vs.85)">CD3D11_DEPTH_STENCIL_DESC</a> structure that is initialized with default depth-stencil-state values.

## -parameters

### -param unnamedParam1

Default depth-stencil-state values.

## -remarks

Here are the default depth-stencil-state values for the members of <a href="/windows/desktop/api/d3d11/ns-d3d11-d3d11_depth_stencil_desc">D3D11_DEPTH_STENCIL_DESC</a>:

```
DepthEnable = TRUE;
        DepthWriteMask = D3D11_DEPTH_WRITE_MASK_ALL;
        DepthFunc = D3D11_COMPARISON_LESS;
        StencilEnable = FALSE;
        StencilReadMask = D3D11_DEFAULT_STENCIL_READ_MASK;
        StencilWriteMask = D3D11_DEFAULT_STENCIL_WRITE_MASK;
        const D3D11_DEPTH_STENCILOP_DESC defaultStencilOp =
        { D3D11_STENCIL_OP_KEEP, D3D11_STENCIL_OP_KEEP, D3D11_STENCIL_OP_KEEP, D3D11_COMPARISON_ALWAYS };
        FrontFace = defaultStencilOp;
        BackFace = defaultStencilOp;

```

## -see-also

<a href="/previous-versions/windows/desktop/legacy/jj151632(v=vs.85)">CD3D11_DEPTH_STENCIL_DESC</a>