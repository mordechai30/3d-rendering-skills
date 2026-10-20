Source: [https://learn.microsoft.com/en-us/windows/win32/api/D3D11SDKLayers/nn-d3d11sdklayers-id3d11debug](<https://learn.microsoft.com/en-us/windows/win32/api/D3D11SDKLayers/nn-d3d11sdklayers-id3d11debug>)

# ID3D11Debug interface


## -description

A debug interface controls debug settings, validates pipeline state and can only be used if the debug layer is turned on.

## -inheritance

The <b>ID3D11Debug</b> interface inherits from the <a href="/windows/desktop/api/unknwn/nn-unknwn-iunknown">IUnknown</a> interface. <b>ID3D11Debug</b> also has these types of members:

## -remarks

This interface is obtained by querying it from the <a href="/windows/desktop/api/d3d11/nn-d3d11-id3d11device">ID3D11Device</a> using <a href="/windows/desktop/api/unknwn/nf-unknwn-iunknown-queryinterface(q)">IUnknown::QueryInterface</a>.
          

For more information about the debug layer, see <a href="/windows/desktop/direct3d11/overviews-direct3d-11-devices-layers">Debug Layer</a>.
          

<b>Windows Phone 8:
        </b> This API is supported.

## -see-also

<a href="/windows/desktop/api/unknwn/nn-unknwn-iunknown">IUnknown</a>



<a href="/windows/desktop/direct3d11/d3d11-graphics-reference-d3d11-layer-interfaces">Layer Interfaces</a>