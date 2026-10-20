Source: [https://learn.microsoft.com/en-us/windows/win32/api/D3D11_1/nf-d3d11_1-id3d11devicecontext1-clearview](<https://learn.microsoft.com/en-us/windows/win32/api/D3D11_1/nf-d3d11_1-id3d11devicecontext1-clearview>)

# ID3D11DeviceContext1::ClearView


## -description

Sets all the elements in a resource view to one value.

## -parameters

### -param pView [in]

A pointer to the <a href="/windows/desktop/api/d3d11/nn-d3d11-id3d11view">ID3D11View</a> interface that represents the resource view to clear.

### -param Color [in]

A 4-component array that represents the color to use to clear the resource view.

### -param pRect [in, optional]

An array of <a href="/windows/desktop/direct3d11/d3d11-rect">D3D11_RECT</a> structures for the rectangles in the resource view to clear. If <b>NULL</b>, <b>ClearView</b> clears the entire surface.

### -param NumRects

Number of rectangles in the array that the  <i>pRect</i> parameter specifies.

## -remarks

<b>ClearView</b> works only on render-target views (RTVs), depth/stencil views (DSVs) on depth-only resources (resources with no stencil component), unordered-access views (UAVs), or any video view of a <a href="/windows/desktop/direct3dhlsl/sm5-object-texture2d">Texture2D</a> surface. The runtime drops invalid calls. Empty rectangles in the <i>pRect</i> array are a no-op. A rectangle is empty if the top value equals the bottom value or the left value equals the right value.

<b>ClearView</b> doesn’t support 3D textures.

<b>ClearView</b> applies the same color value to all array slices in a view; all rectangles in the <i>pRect</i> array correspond to each array slice.  The <i>pRect</i> array of rectangles is a set of areas to clear on a single surface.  If the view is an array, <b>ClearView</b> clears all the rectangles on each array slice individually.

When you apply rectangles to buffers, set the top value to 0 and the bottom value to 1 and set the left value and right value to describe the extent within the buffer. When the top value equals the bottom value or the left value equals the right value, the rectangle is empty and a no-op is achieved.

The driver converts and clamps color values to the destination format as appropriate per Direct3D conversion rules.  For example, if the format of the view is <a href="/windows/desktop/api/dxgiformat/ne-dxgiformat-dxgi_format">DXGI_FORMAT_R8G8B8A8_UNORM</a>, the driver clamps inputs to 0.0f to 1.0f (+INF -&gt; 1.0f (0XFF)/NaN -&gt; 0.0f).

If the format is integer, such as <a href="/windows/desktop/api/dxgiformat/ne-dxgiformat-dxgi_format">DXGI_FORMAT_R8G8B8A8_UINT</a>, the runtime interprets inputs as integral floats. Therefore, 235.0f maps to 235 (rounds to zero, out of range/INF values clamp to target range, and NaN to 0).

Here are the color mappings:

<ul>
<li>Color[0]: R (or Y for video)</li>
<li>Color[1]: G (or U/Cb for video)</li>
<li>Color[2]: B (or V/Cr for video)</li>
<li>Color[3]: A</li>
</ul>
For video views with YUV or YCbBr formats, <b>ClearView</b> doesn't convert color values. In situations where the format name doesn’t indicate _UNORM,  _UINT, and so on, <b>ClearView</b> assumes _UINT. Therefore, 235.0f maps to 235 (rounds to zero, out of range/INF values clamp to target range, and NaN to 0).

## -see-also

<a href="/windows/desktop/api/d3d11_1/nn-d3d11_1-id3d11devicecontext1">ID3D11DeviceContext1</a>