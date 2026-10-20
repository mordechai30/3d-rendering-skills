Source: [https://learn.microsoft.com/en-us/windows/win32/api/D3D11SDKLayers/nn-d3d11sdklayers-id3d11tracingdevice](<https://learn.microsoft.com/en-us/windows/win32/api/D3D11SDKLayers/nn-d3d11sdklayers-id3d11tracingdevice>)

# ID3D11TracingDevice interface


## -description

The tracing device interface sets shader tracking information, which enables accurate logging and playback of shader execution.

## -inheritance

The <b>ID3D11TracingDevice</b> interface inherits from the <a href="/windows/desktop/api/unknwn/nn-unknwn-iunknown">IUnknown</a> interface. <b>ID3D11TracingDevice</b> also has these types of members:

## -remarks

To get this interface, turn on the <a href="/windows/desktop/direct3d11/overviews-direct3d-11-devices-layers">debug layer</a> and use <a href="/windows/desktop/api/unknwn/nf-unknwn-iunknown-queryinterface(q)">IUnknown::QueryInterface</a> from the <a href="/windows/desktop/api/d3d11/nn-d3d11-id3d11device">ID3D11Device</a>.

<div class="alert"><b>Note</b>  This API requires the Windows Software Development Kit (SDK) for Windows 8.</div>
<div> </div>

## -see-also

<a href="/windows/desktop/api/unknwn/nn-unknwn-iunknown">IUnknown</a>



<a href="/windows/desktop/direct3d11/d3d11-graphics-reference-d3d11-layer-interfaces">Layer Interfaces</a>