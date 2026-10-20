Source: [https://learn.microsoft.com/en-us/windows/win32/api/d3d11/nf-d3d11-cd3d11_rasterizer_desc-cd3d11_rasterizer_desc(cd3d11_default)](<https://learn.microsoft.com/en-us/windows/win32/api/d3d11/nf-d3d11-cd3d11_rasterizer_desc-cd3d11_rasterizer_desc(cd3d11_default)>)

# CD3D11_RASTERIZER_DESC::CD3D11_RASTERIZER_DESC(CD3D11_DEFAULT)


## -description

Instantiates a new instance of a <a href="/previous-versions/windows/desktop/legacy/jj151654(v=vs.85)">CD3D11_RASTERIZER_DESC</a> structure that is initialized with default rasterizer-state values.

## -parameters

### -param unnamedParam1

Address of the **D3D11_RASTERIZER_DESC** structure that initializes the **CD3D11_RASTERIZER_DESC** structure.

## -remarks

Here are the default rasterizer-state values for the members of <a href="/windows/desktop/api/d3d11/ns-d3d11-d3d11_rasterizer_desc">D3D11_RASTERIZER_DESC</a>:

```
FillMode = D3D11_FILL_SOLID;
        CullMode = D3D11_CULL_BACK;
        FrontCounterClockwise = FALSE;
        DepthBias = D3D11_DEFAULT_DEPTH_BIAS;
        DepthBiasClamp = D3D11_DEFAULT_DEPTH_BIAS_CLAMP;
        SlopeScaledDepthBias = D3D11_DEFAULT_SLOPE_SCALED_DEPTH_BIAS;
        DepthClipEnable = TRUE;
        ScissorEnable = FALSE;
        MultisampleEnable = FALSE;
        AntialiasedLineEnable = FALSE;

```

## -see-also

<a href="/previous-versions/windows/desktop/legacy/jj151654(v=vs.85)">CD3D11_RASTERIZER_DESC</a>