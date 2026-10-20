Source: [https://learn.microsoft.com/en-us/windows/win32/api/D3D11/nf-d3d11-id3d11devicecontext-rsgetviewports](<https://learn.microsoft.com/en-us/windows/win32/api/D3D11/nf-d3d11-id3d11devicecontext-rsgetviewports>)

# ID3D11DeviceContext::RSGetViewports


## -description

Gets the array of viewports bound to the rasterizer stage.

## -parameters

### -param pNumViewports [in, out]

Type: <b><a href="/windows/desktop/WinProg/windows-data-types">UINT</a>*</b>

A pointer to a variable that, on input, specifies the number of viewports (ranges from 0 to <b>D3D11_VIEWPORT_AND_SCISSORRECT_OBJECT_COUNT_PER_PIPELINE</b>)
            in the <i>pViewports</i> array; on output, the variable contains the actual number of viewports that are bound to the rasterizer stage.
            If <i>pViewports</i> is <b>NULL</b>, <b>RSGetViewports</b> fills the variable with the number of viewports currently bound.

<div class="alert"><b>Note</b>  In some versions of the Windows SDK, a <a href="/windows/desktop/direct3d11/overviews-direct3d-11-devices-layers">debug device</a> will raise an exception if the input value in the variable to which <i>pNumViewports</i> points is greater than <b>D3D11_VIEWPORT_AND_SCISSORRECT_OBJECT_COUNT_PER_PIPELINE</b> even if <i>pViewports</i> is <b>NULL</b>.  The regular runtime ignores the value in the variable to which <i>pNumViewports</i> points when <i>pViewports</i> is <b>NULL</b>.  This behavior of a debug device might be corrected in a future release of the Windows SDK.
            </div>
<div> </div>

### -param pViewports [out, optional]

Type: <b><a href="/windows/desktop/api/d3d11/ns-d3d11-d3d11_viewport">D3D11_VIEWPORT</a>*</b>

An array of <a href="/windows/desktop/api/d3d11/ns-d3d11-d3d11_viewport">D3D11_VIEWPORT</a> structures for the viewports that are bound to the rasterizer stage. If the number of viewports (in the variable to which <i>pNumViewports</i> points) is
            greater than the actual number of viewports currently bound, unused elements of the array contain 0.
            For info about how the viewport size depends on the device <a href="/windows/desktop/direct3d11/overviews-direct3d-11-devices-downlevel-intro">feature level</a>, which has changed between Direct3D 11
            and Direct3D 10, see <b>D3D11_VIEWPORT</b>.

## -remarks

<b>Windows Phone 8:
        </b> This API is supported.

## -see-also

<a href="/windows/desktop/api/d3d11/nn-d3d11-id3d11devicecontext">ID3D11DeviceContext</a>