Source: [https://learn.microsoft.com/en-us/windows/win32/api/D3D11/nf-d3d11-id3d11devicecontext-clearrendertargetview](<https://learn.microsoft.com/en-us/windows/win32/api/D3D11/nf-d3d11-id3d11devicecontext-clearrendertargetview>)

# ID3D11DeviceContext::ClearRenderTargetView


## -description

Set all the elements in a render target to one value.

## -parameters

### -param pRenderTargetView [in]

Type: <b><a href="/windows/desktop/api/d3d11/nn-d3d11-id3d11rendertargetview">ID3D11RenderTargetView</a>*</b>

Pointer to the render target.

### -param ColorRGBA [in]

Type: <b>const <a href="/windows/desktop/WinProg/windows-data-types">FLOAT</a>[4]</b>

A 4-component array that represents the color to fill the render target with.

## -remarks

Applications that wish to clear a render target to a specific integer value bit pattern should render a screen-aligned quad instead of using this method.  The reason for this is because this method accepts as input a floating point value, which may not have the same bit pattern as the original integer.

<table>
<tr>
<td>
Differences between Direct3D 9 and Direct3D 11/10:

Unlike Direct3D 9, the full extent of the resource view is always cleared. Viewport and scissor settings are not applied.

</td>
</tr>
</table>
 

When using <a href="/windows/desktop/api/d3dcommon/ne-d3dcommon-d3d_feature_level">D3D_FEATURE_LEVEL_9_x</a>, <a href="/windows/desktop/api/d3d10/nf-d3d10-id3d10device-clearrendertargetview">ClearRenderTargetView</a> only clears the first array slice in the render target view. This can impact (for example) cube map rendering scenarios. Applications should create a render target view for each face or array slice, then clear each view individually.

## -see-also

<a href="/windows/desktop/api/d3d11/nn-d3d11-id3d11devicecontext">ID3D11DeviceContext</a>