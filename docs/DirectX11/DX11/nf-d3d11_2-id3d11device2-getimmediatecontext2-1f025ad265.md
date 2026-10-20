Source: [https://learn.microsoft.com/en-us/windows/win32/api/D3D11_2/nf-d3d11_2-id3d11device2-getimmediatecontext2](<https://learn.microsoft.com/en-us/windows/win32/api/D3D11_2/nf-d3d11_2-id3d11device2-getimmediatecontext2>)

# ID3D11Device2::GetImmediateContext2


## -description

Gets an immediate context, which can play back <a href="/windows/desktop/direct3d11/overviews-direct3d-11-render-multi-thread-command-list">command lists</a>.

## -parameters

### -param ppImmediateContext [out]

Type: <b><a href="/windows/desktop/api/d3d11_2/nn-d3d11_2-id3d11devicecontext2">ID3D11DeviceContext2</a>**</b>

Upon completion of the method, the passed pointer to an <a href="/windows/desktop/api/d3d11_2/nn-d3d11_2-id3d11devicecontext2">ID3D11DeviceContext2</a> interface pointer is initialized.

## -remarks

The <b>GetImmediateContext2</b> method returns an <a href="/windows/desktop/api/d3d11_2/nn-d3d11_2-id3d11devicecontext2">ID3D11DeviceContext2</a> object that represents an immediate context, which is used to perform rendering that you want immediately submitted to a device. For most apps, an immediate context is the primary object that is used to draw your scene.

The <b>GetImmediateContext2</b> method increments the reference count of the immediate context by one. Therefore, you must call <a href="/windows/desktop/api/unknwn/nf-unknwn-iunknown-release">Release</a> on the returned interface pointer when you are done with it to avoid a memory leak.

## -see-also

<a href="/windows/desktop/api/d3d11_2/nn-d3d11_2-id3d11device2">ID3D11Device2</a>