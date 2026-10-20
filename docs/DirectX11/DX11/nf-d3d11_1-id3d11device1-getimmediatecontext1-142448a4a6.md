Source: [https://learn.microsoft.com/en-us/windows/win32/api/D3D11_1/nf-d3d11_1-id3d11device1-getimmediatecontext1](<https://learn.microsoft.com/en-us/windows/win32/api/D3D11_1/nf-d3d11_1-id3d11device1-getimmediatecontext1>)

# ID3D11Device1::GetImmediateContext1


## -description

Gets an immediate context, which can play back command lists.

## -parameters

### -param ppImmediateContext [out]

Upon completion of the method, the passed pointer to an <a href="/windows/desktop/api/d3d11_1/nn-d3d11_1-id3d11devicecontext1">ID3D11DeviceContext1</a> interface pointer is initialized.

## -remarks

<b>GetImmediateContext1</b> returns an <a href="/windows/desktop/api/d3d11_1/nn-d3d11_1-id3d11devicecontext1">ID3D11DeviceContext1</a> object that represents an immediate context. You can use this immediate context to perform rendering that you want immediately submitted to a device. For most applications, an immediate context is the primary object that is used to draw your scene.

<b>GetImmediateContext1</b> increments the reference count of the immediate context by one. So, call <a href="/windows/desktop/api/unknwn/nf-unknwn-iunknown-release">Release</a> on the returned interface pointer when you are done with it to avoid a memory leak.

## -see-also

<a href="/windows/desktop/api/d3d11_1/nn-d3d11_1-id3d11device1">ID3D11Device1</a>