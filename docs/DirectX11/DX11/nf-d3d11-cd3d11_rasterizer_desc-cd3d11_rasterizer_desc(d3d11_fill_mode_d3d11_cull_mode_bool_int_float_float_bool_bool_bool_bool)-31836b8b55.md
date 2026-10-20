Source: [https://learn.microsoft.com/en-us/windows/win32/api/d3d11/nf-d3d11-cd3d11_rasterizer_desc-cd3d11_rasterizer_desc(d3d11_fill_mode_d3d11_cull_mode_bool_int_float_float_bool_bool_bool_bool)](<https://learn.microsoft.com/en-us/windows/win32/api/d3d11/nf-d3d11-cd3d11_rasterizer_desc-cd3d11_rasterizer_desc(d3d11_fill_mode_d3d11_cull_mode_bool_int_float_float_bool_bool_bool_bool)>)

# CD3D11_RASTERIZER_DESC::CD3D11_RASTERIZER_DESC(D3D11_FILL_MODE,D3D11_CULL_MODE,BOOL,INT,FLOAT,FLOAT,BOOL,BOOL,BOOL,BOOL)


## -description

Instantiates a new instance of a <a href="/previous-versions/windows/desktop/legacy/jj151654(v=vs.85)">CD3D11_RASTERIZER_DESC</a> structure that is initialized with <a href="/windows/desktop/api/d3d11/ns-d3d11-d3d11_rasterizer_desc">D3D11_RASTERIZER_DESC</a> values.

## -parameters

### -param fillMode

Type: <b><a href="/windows/desktop/api/d3d11/ne-d3d11-d3d11_fill_mode">D3D11_FILL_MODE</a></b>

A <a href="/windows/desktop/api/d3d11/ne-d3d11-d3d11_fill_mode">D3D11_FILL_MODE</a>-typed value that determines the fill mode to use when rendering.

### -param cullMode

Type: <b><a href="/windows/desktop/api/d3d11/ne-d3d11-d3d11_cull_mode">D3D11_CULL_MODE</a></b>

A <a href="/windows/desktop/api/d3d11/ne-d3d11-d3d11_cull_mode">D3D11_CULL_MODE</a>-typed value that indicates triangles facing the specified direction are not drawn.

### -param frontCounterClockwise

Type: <b><a href="/windows/desktop/WinProg/windows-data-types">BOOL</a></b>

A Boolean value that specifies whether a triangle is front- or back-facing. If this parameter is <b>TRUE</b>, a triangle will be considered front-facing if its vertices are counter-clockwise on the render target and considered back-facing if they are clockwise. If this parameter is <b>FALSE</b>, the opposite is true.

### -param depthBias

Type: <b><a href="/windows/desktop/WinProg/windows-data-types">INT</a></b>

Depth value added to a given pixel. For info about depth bias, see <a href="/windows/desktop/direct3d11/d3d10-graphics-programming-guide-output-merger-stage-depth-bias">Depth Bias</a>.

### -param depthBiasClamp

Type: <b><a href="/windows/desktop/WinProg/windows-data-types">FLOAT</a></b>

Maximum depth bias of a pixel. For info about depth bias, see <a href="/windows/desktop/direct3d11/d3d10-graphics-programming-guide-output-merger-stage-depth-bias">Depth Bias</a>.

### -param slopeScaledDepthBias

Type: <b><a href="/windows/desktop/WinProg/windows-data-types">FLOAT</a></b>

Scalar on a given pixel's slope. For info about depth bias, see <a href="/windows/desktop/direct3d11/d3d10-graphics-programming-guide-output-merger-stage-depth-bias">Depth Bias</a>.

### -param depthClipEnable

Type: <b><a href="/windows/desktop/WinProg/windows-data-types">BOOL</a></b>

A Boolean value that specifies whether to enable clipping based on distance.

The hardware always performs x and y clipping of rasterized coordinates. When <i>depthClipEnable</i> is set to the default–<b>TRUE</b>, the hardware also clips the z value (that is, the hardware performs the last step of the following algorithm).



``` syntax

0 < w
-w <= x <= w (or arbitrarily wider range if implementation uses a guard band to reduce clipping burden)
-w <= y <= w (or arbitrarily wider range if implementation uses a guard band to reduce clipping burden)
0 <= z <= w

```

When you set <i>depthClipEnable</i> to <b>FALSE</b>, the hardware skips the z clipping (that is, the last step in the preceding algorithm). However, the hardware still performs the "0 &lt; w" clipping. When z clipping is disabled, improper depth ordering at the pixel level might result. However, when z clipping is disabled, stencil shadow implementations are simplified. In other words, you can avoid complex special-case handling for geometry that goes beyond the back clipping plane.

### -param scissorEnable

Type: <b><a href="/windows/desktop/WinProg/windows-data-types">BOOL</a></b>

A Boolean value that specifies whether to enable scissor-rectangle culling. All pixels outside an active scissor rectangle are culled.

### -param multisampleEnable

Type: <b><a href="/windows/desktop/WinProg/windows-data-types">BOOL</a></b>

A Boolean value that specifies whether to use the quadrilateral or alpha line anti-aliasing algorithm on multisample antialiasing (MSAA) render targets. Set to <b>TRUE</b> to use the quadrilateral line anti-aliasing algorithm and to <b>FALSE</b> to use the alpha line anti-aliasing algorithm.

### -param antialiasedLineEnable

Type: <b><a href="/windows/desktop/WinProg/windows-data-types">BOOL</a></b>

A Boolean value that specifies whether to enable line antialiasing; only applies if doing line drawing and <i>multisampleEnable</i> is <b>FALSE</b>.

## -remarks

Here is how CD3D11_RASTERIZER_DESC assigns the provided values to the members of <a href="/windows/desktop/api/d3d11/ns-d3d11-d3d11_rasterizer_desc">D3D11_RASTERIZER_DESC</a>:


```
FillMode = fillMode;
        CullMode = cullMode;
        FrontCounterClockwise = frontCounterClockwise;
        DepthBias = depthBias;
        DepthBiasClamp = depthBiasClamp;
        SlopeScaledDepthBias = slopeScaledDepthBias;
        DepthClipEnable = depthClipEnable;
        ScissorEnable = scissorEnable;
        MultisampleEnable = multisampleEnable;
        AntialiasedLineEnable = antialiasedLineEnable;

```

## -see-also

<a href="/previous-versions/windows/desktop/legacy/jj151654(v=vs.85)">CD3D11_RASTERIZER_DESC</a>