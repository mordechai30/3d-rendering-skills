Source: [https://learn.microsoft.com/en-us/windows/win32/direct3d11/d3d10-graphics-programming-guide-rasterizer-stage](<https://learn.microsoft.com/en-us/windows/win32/direct3d11/d3d10-graphics-programming-guide-rasterizer-stage>)

# Rasterizer Stage

The rasterization stage converts vector information (composed of shapes or primitives) into a raster image (composed of pixels) for the purpose of displaying real-time 3D graphics.

During rasterization, each primitive is converted into pixels, while interpolating per-vertex values across each primitive. Rasterization includes clipping vertices to the view frustum, performing a divide by z to provide perspective, mapping primitives to a 2D viewport, and determining how to invoke the pixel shader. While using a pixel shader is optional, the rasterizer stage always performs clipping, a perspective divide to transform the points into homogeneous space, and maps the vertices to the viewport.

Vertices (x,y,z,w), coming into the rasterizer stage are assumed to be in homogeneous clip-space. In this coordinate space the X axis points right, Y points up and Z points away from camera.

You may disable rasterization by telling the pipeline there is no pixel shader (set the pixel shader stage to **NULL** with [**ID3D11DeviceContext::PSSetShader**](./nf-d3d11-id3d11devicecontext-pssetshader-830ddd515f.md)), and disabling depth and stencil testing (set **DepthEnable** and **StencilEnable** to **FALSE** in [**D3D11\_DEPTH\_STENCIL\_DESC**](./ns-d3d11-d3d11_depth_stencil_desc-e5f1b30def.md)). While disabled, rasterization-related pipeline counters will not update. There is also a complete description of the [rasterization rules](./d3d10-graphics-programming-guide-rasterizer-stage-rules-2095cdb512.md).

On hardware that implements hierarchical Z-buffer optimizations, you may enable preloading the z-buffer by setting the pixel shader stage to **NULL** while enabling depth and stencil testing.


## In this section



| Topic                                                                                                                         | Description                                                                                                                                                                                                                                                                                                              |
|-------------------------------------------------------------------------------------------------------------------------------|--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| [Getting Started with the Rasterizer Stage](./d3d10-graphics-programming-guide-rasterizer-stage-getting-started-ebb8d854b6.md)<br/> | This section describes setting the viewport, the scissors rectangle, the rasterizer state, and multi-sampling.<br/>                                                                                                                                                                                                |
| [Rasterization Rules](./d3d10-graphics-programming-guide-rasterizer-stage-rules-2095cdb512.md)<br/>                                 | Rasterization rules define how vector data is mapped into raster data. The raster data is snapped to integer locations that are then culled and clipped (to draw the minimum number of pixels), and per-pixel attributes are interpolated (from per-vertex attributes) before being passed to a pixel shader.<br/> |



 

## Related topics

<dl> <dt>

[Graphics Pipeline](./overviews-direct3d-11-graphics-pipeline-afe69eb859.md)
</dt> <dt>

[Pipeline Stages (Direct3D 10)](/windows/desktop/direct3d10/d3d10-graphics-programming-guide-pipeline-stages)
</dt> </dl>