Source: [https://learn.microsoft.com/en-us/windows/win32/api/D3D11/nf-d3d11-id3d11devicecontext-cleardepthstencilview](<https://learn.microsoft.com/en-us/windows/win32/api/D3D11/nf-d3d11-id3d11devicecontext-cleardepthstencilview>)

# ID3D11DeviceContext::ClearDepthStencilView


## -description

Clears the depth-stencil resource.

## -parameters

### -param pDepthStencilView [in]

Type: <b><a href="/windows/desktop/api/d3d11/nn-d3d11-id3d11depthstencilview">ID3D11DepthStencilView</a>*</b>

Pointer to the depth stencil to be cleared.

### -param ClearFlags [in]

Type: <b><a href="/windows/desktop/WinProg/windows-data-types">UINT</a></b>

Identify the type of data to clear (see <a href="/windows/desktop/api/d3d11/ne-d3d11-d3d11_clear_flag">D3D11_CLEAR_FLAG</a>).

### -param Depth [in]

Type: <b><a href="/windows/desktop/WinProg/windows-data-types">FLOAT</a></b>

Clear the depth buffer with this value. This value will be clamped between 0 and 1.

### -param Stencil [in]

Type: <b>UINT8</b>

Clear the stencil buffer with this value.

## -remarks

<table>
<tr>
<td>
Differences between Direct3D 9 and Direct3D 11/10:

Unlike Direct3D 9, the full extent of the resource view is always cleared. Viewport and scissor settings are not applied.

</td>
</tr>
</table>

## -see-also

<a href="/windows/desktop/api/d3d11/nn-d3d11-id3d11devicecontext">ID3D11DeviceContext</a>