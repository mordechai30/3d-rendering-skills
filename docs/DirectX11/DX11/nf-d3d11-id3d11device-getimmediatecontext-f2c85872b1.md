Source: [https://learn.microsoft.com/en-us/windows/win32/api/D3D11/nf-d3d11-id3d11device-getimmediatecontext](<https://learn.microsoft.com/en-us/windows/win32/api/D3D11/nf-d3d11-id3d11device-getimmediatecontext>)

# ID3D11Device::GetImmediateContext


## -description

Gets an immediate context, which can play back command lists.

## -parameters

### -param ppImmediateContext [out]

Type: <b><a href="/windows/desktop/api/d3d11/nn-d3d11-id3d11devicecontext">ID3D11DeviceContext</a>**</b>

Upon completion of the method, the passed pointer to an <a href="/windows/desktop/api/d3d11/nn-d3d11-id3d11devicecontext">ID3D11DeviceContext</a> interface pointer is initialized.

## -remarks

The <b>GetImmediateContext</b> method returns an <a href="/windows/desktop/api/d3d11/nn-d3d11-id3d11devicecontext">ID3D11DeviceContext</a> object that represents an immediate context which is used to perform rendering that you want immediately submitted to a device. For most applications, an immediate context is the primary object that is used to draw your scene.

The <b>GetImmediateContext</b> method increments the reference count of the immediate context by one. Therefore, you must call <a href="/windows/desktop/api/unknwn/nf-unknwn-iunknown-release">Release</a> on the returned interface pointer when you are done with it to avoid a memory leak.

## -see-also

<a href="/windows/desktop/api/d3d11/nn-d3d11-id3d11device">ID3D11Device</a>