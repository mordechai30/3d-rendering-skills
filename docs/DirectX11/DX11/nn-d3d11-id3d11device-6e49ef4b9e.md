Source: [https://learn.microsoft.com/en-us/windows/win32/api/D3D11/nn-d3d11-id3d11device](<https://learn.microsoft.com/en-us/windows/win32/api/D3D11/nn-d3d11-id3d11device>)

# ID3D11Device interface


## -description

The device interface represents a virtual adapter; it is used to create resources.
<div class="alert"><b>Note</b>  The latest version of this interface is <a href="/windows/desktop/api/d3d11_4/nn-d3d11_4-id3d11device5">ID3D11Device5</a> introduced in the Windows 10 Creators Update. Applications targetting Windows 10 Creators Update should use the <b>ID3D11Device5</b> interface instead of <b>ID3D11Device</b>.</div><div> </div>

## -inheritance

The <b>ID3D11Device</b> interface inherits from the <a href="/windows/desktop/api/unknwn/nn-unknwn-iunknown">IUnknown</a> interface. <b>ID3D11Device</b> also has these types of members:

## -remarks

A device is created using <a href="/windows/desktop/api/d3d11/nf-d3d11-d3d11createdevice">D3D11CreateDevice</a>.
          

<b>Windows Phone 8:
        </b> This API is supported.

## -see-also

<a href="/windows/desktop/direct3d11/d3d11-graphics-reference-d3d11-core-interfaces">Core Interfaces</a>



<a href="/windows/desktop/api/unknwn/nn-unknwn-iunknown">IUnknown</a>