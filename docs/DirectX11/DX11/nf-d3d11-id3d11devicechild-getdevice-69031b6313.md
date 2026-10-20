Source: [https://learn.microsoft.com/en-us/windows/win32/api/D3D11/nf-d3d11-id3d11devicechild-getdevice](<https://learn.microsoft.com/en-us/windows/win32/api/D3D11/nf-d3d11-id3d11devicechild-getdevice>)

# ID3D11DeviceChild::GetDevice


## -description

Get a pointer to the device that created this interface.

## -parameters

### -param ppDevice [out]

Type: <b><a href="/windows/desktop/api/d3d11/nn-d3d11-id3d11device">ID3D11Device</a>**</b>

Address of a pointer to a device (see <a href="/windows/desktop/api/d3d11/nn-d3d11-id3d11device">ID3D11Device</a>).

## -remarks

Any returned interfaces will have their reference count incremented by one, so be sure to call ::release() on the returned pointer(s) before they are freed or else you will have a memory leak.

## -see-also

<a href="/windows/desktop/api/d3d11/nn-d3d11-id3d11devicechild">ID3D11DeviceChild</a>