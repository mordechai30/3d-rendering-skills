Source: [https://learn.microsoft.com/en-us/windows/win32/api/d3d11_3/nf-d3d11_3-id3d11device3-getimmediatecontext3](<https://learn.microsoft.com/en-us/windows/win32/api/d3d11_3/nf-d3d11_3-id3d11device3-getimmediatecontext3>)

# ID3D11Device3::GetImmediateContext3


## -description

Gets an immediate context, which can play back <a href="/windows/desktop/direct3d11/overviews-direct3d-11-render-multi-thread-command-list">command lists</a>.

## -parameters

### -param ppImmediateContext [out]

Type: <b><a href="/windows/desktop/api/d3d11_3/nn-d3d11_3-id3d11devicecontext3">ID3D11DeviceContext3</a>**</b>

Upon completion of the method, the passed pointer to an <a href="/windows/desktop/api/d3d11_3/nn-d3d11_3-id3d11devicecontext3">ID3D11DeviceContext3</a> interface pointer is initialized.

## -remarks

The
         <b>GetImmediateContext3</b> method outputs an
          <a href="/windows/desktop/api/d3d11_3/nn-d3d11_3-id3d11devicecontext3">ID3D11DeviceContext3</a> object that represents an immediate context, which is used to perform rendering that you want immediately submitted to a device.
          For most apps, an immediate context is the primary object that is used to draw your scene.
        

The <b>GetImmediateContext3</b> method increments the reference count of the immediate context by one.
          Therefore, you must call <a href="/windows/desktop/api/unknwn/nf-unknwn-iunknown-release">Release</a> on the returned interface pointer when you are done with it to avoid a memory leak.

## -see-also

<a href="/windows/desktop/api/d3d11_1/nf-d3d11_1-id3d11device1-getimmediatecontext1">ID3D11Device1::GetImmediateContext1</a>



<a href="/windows/desktop/api/d3d11_2/nf-d3d11_2-id3d11device2-getimmediatecontext2">ID3D11Device2::GetImmediateContext2</a>



<a href="/windows/desktop/api/d3d11_3/nn-d3d11_3-id3d11device3">ID3D11Device3</a>



<a href="/windows/desktop/api/d3d11/nf-d3d11-id3d11device-getimmediatecontext">ID3D11Device::GetImmediateContext</a>