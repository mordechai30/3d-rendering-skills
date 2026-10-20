Source: [https://learn.microsoft.com/en-us/windows/win32/api/D3D11/nf-d3d11-id3d11device-getdeviceremovedreason](<https://learn.microsoft.com/en-us/windows/win32/api/D3D11/nf-d3d11-id3d11device-getdeviceremovedreason>)

# ID3D11Device::GetDeviceRemovedReason


## -description

Get the reason why the device was removed.



## -returns

Type: <b><a href="/windows/win32/com/structure-of-com-error-codes">HRESULT</a></b>

Possible return values include: 



<ul>
<li>DXGI_ERROR_DEVICE_HUNG</li>
<li>DXGI_ERROR_DEVICE_REMOVED</li>
<li>DXGI_ERROR_DEVICE_RESET</li>
<li>DXGI_ERROR_DRIVER_INTERNAL_ERROR</li>
<li>DXGI_ERROR_INVALID_CALL</li>
<li>S_OK</li>
</ul>
For more detail on these return codes, see <a href="/windows/desktop/direct3ddxgi/dxgi-error">DXGI_ERROR</a>.

## -see-also

<a href="/windows/desktop/api/d3d11/nn-d3d11-id3d11device">ID3D11Device</a>