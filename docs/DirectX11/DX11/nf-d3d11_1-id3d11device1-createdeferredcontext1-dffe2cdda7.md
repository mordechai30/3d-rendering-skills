Source: [https://learn.microsoft.com/en-us/windows/win32/api/D3D11_1/nf-d3d11_1-id3d11device1-createdeferredcontext1](<https://learn.microsoft.com/en-us/windows/win32/api/D3D11_1/nf-d3d11_1-id3d11device1-createdeferredcontext1>)

# ID3D11Device1::CreateDeferredContext1


## -description

Creates a deferred context, which can record command lists.

## -parameters

### -param ContextFlags

Reserved for future use.
            Pass 0.

### -param ppDeferredContext [out, optional]

Upon completion of the method, the passed pointer to an <a href="/windows/desktop/api/d3d11_1/nn-d3d11_1-id3d11devicecontext1">ID3D11DeviceContext1</a> interface pointer is initialized.

## -returns

Returns S_OK if successful; otherwise, returns one of the following:
            

<ul>
<li>Returns <b>DXGI_ERROR_DEVICE_REMOVED</b> if the graphics adapter has been physically removed from the computer or a driver upgrade for the graphics adapter has occurred.
                If this error occurs, you should destroy and re-create the device.
              </li>
<li>Returns <b>DXGI_ERROR_INVALID_CALL</b> if the <b>CreateDeferredContext1</b> method cannot be called from the current context.
                For example, if the device was created with the <a href="/windows/desktop/api/d3d11/ne-d3d11-d3d11_create_device_flag">D3D11_CREATE_DEVICE_SINGLETHREADED</a> value,  <b>CreateDeferredContext1</b> returns <b>DXGI_ERROR_INVALID_CALL</b>.
              </li>
<li>Returns <b>E_INVALIDARG</b> if the <i>ContextFlags</i> parameter is invalid.
              </li>
<li>Returns <b>E_OUTOFMEMORY</b> if the application has exhausted available memory.
              </li>
</ul>

## -remarks

A deferred context is a thread-safe context that you can use to record graphics commands on a thread other than the main rendering thread.
          By using a deferred context, you can record graphics commands into a command list that is encapsulated by the <a href="/windows/desktop/api/d3d11/nn-d3d11-id3d11commandlist">ID3D11CommandList</a> interface.
          After you record all scene items, you can then submit them to the main render thread for final rendering.
          In this manner, you can perform rendering tasks concurrently across multiple threads and potentially improve performance in multi-core CPU scenarios.
        

You can create multiple deferred contexts.
        

<div class="alert"><b>Note</b>  If you use the <a href="/windows/desktop/api/d3d11/ne-d3d11-d3d11_create_device_flag">D3D11_CREATE_DEVICE_SINGLETHREADED</a> value to create the device that is represented by <a href="/windows/desktop/api/d3d11_1/nn-d3d11_1-id3d11device1">ID3D11Device1</a>, the <b>CreateDeferredContext1</b> method will fail, and you will not be able to create a deferred context.
        </div>
<div> </div>
For more information about deferred contexts, see <a href="/windows/desktop/direct3d11/overviews-direct3d-11-render-multi-thread-render">Immediate and Deferred Rendering</a>.
        

<b>Windows Phone 8:
        </b> This API is supported.

## -see-also

<a href="/windows/desktop/api/d3d11_1/nn-d3d11_1-id3d11device1">ID3D11Device1</a>



<a href="/windows/desktop/api/d3d11_2/nf-d3d11_2-id3d11device2-createdeferredcontext2">ID3D11Device2::CreateDeferredContext2</a>



<a href="/windows/desktop/api/d3d11_3/nf-d3d11_3-id3d11device3-createdeferredcontext3">ID3D11Device3::CreateDeferredContext3</a>



<a href="/windows/desktop/api/d3d11/nf-d3d11-id3d11device-createdeferredcontext">ID3D11Device::CreateDeferredContext</a>