Source: [https://learn.microsoft.com/en-us/windows/win32/api/D3D11SDKLayers/nn-d3d11sdklayers-id3d11infoqueue](<https://learn.microsoft.com/en-us/windows/win32/api/D3D11SDKLayers/nn-d3d11sdklayers-id3d11infoqueue>)

# ID3D11InfoQueue interface


## -description

An information-queue interface stores, retrieves, and filters debug messages. The queue consists of a message queue, an optional storage filter stack, and a optional retrieval filter stack.

## -inheritance

The <b>ID3D11InfoQueue</b> interface inherits from the <a href="/windows/desktop/api/unknwn/nn-unknwn-iunknown">IUnknown</a> interface. <b>ID3D11InfoQueue</b> also has these types of members:

## -remarks

To get this interface, turn on debug layer and use <a href="/windows/desktop/api/unknwn/nf-unknwn-iunknown-queryinterface(q)">IUnknown::QueryInterface</a> from the <a href="/windows/desktop/api/d3d11/nn-d3d11-id3d11device">ID3D11Device</a>.
          

<b>Windows Phone 8:
        </b> This API is supported.

## -see-also

<a href="/windows/desktop/api/unknwn/nn-unknwn-iunknown">IUnknown</a>



<a href="/windows/desktop/direct3d11/d3d11-graphics-reference-d3d11-layer-interfaces">Layer Interfaces</a>