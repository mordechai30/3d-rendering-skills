Source: [https://learn.microsoft.com/en-us/windows/win32/api/D3D11/nf-d3d11-id3d11device-getprivatedata](<https://learn.microsoft.com/en-us/windows/win32/api/D3D11/nf-d3d11-id3d11device-getprivatedata>)

# ID3D11Device::GetPrivateData


## -description

Get application-defined data from a device.

## -parameters

### -param guid [in]

Type: <b><a href="/openspecs/windows_protocols/ms-oaut/6e7d7108-c213-40bc-8294-ac13fe68fd50">REFGUID</a></b>

Guid associated with the data.

### -param pDataSize [in, out]

Type: <b><a href="/windows/desktop/WinProg/windows-data-types">UINT</a>*</b>

A pointer to a variable that on input contains the size, in bytes, of the buffer that <i>pData</i> points to, and on output contains the size, in bytes, of the amount of data that <b>GetPrivateData</b> retrieved.

### -param pData [out, optional]

Type: <b>void*</b>

A pointer to a buffer that <b>GetPrivateData</b>  fills with data from the device if <i>pDataSize</i> points to a value that specifies a buffer large enough to hold the data.

## -returns

Type: <b><a href="/windows/win32/com/structure-of-com-error-codes">HRESULT</a></b>

This method returns one of the codes described in the topic <a href="/windows/desktop/direct3d11/d3d11-graphics-reference-returnvalues">Direct3D 11 Return Codes</a>.

## -remarks

If the data returned is a pointer to an <a href="/windows/desktop/api/unknwn/nn-unknwn-iunknown">IUnknown</a>, or one of its derivative classes, which was previously set by **SetPrivateDataInterface**, that interface will have its reference count incremented before the private data is returned.

## -see-also

<a href="/windows/desktop/api/d3d11/nn-d3d11-id3d11device">ID3D11Device</a>