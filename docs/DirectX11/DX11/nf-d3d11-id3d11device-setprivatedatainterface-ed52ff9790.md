Source: [https://learn.microsoft.com/en-us/windows/win32/api/D3D11/nf-d3d11-id3d11device-setprivatedatainterface](<https://learn.microsoft.com/en-us/windows/win32/api/D3D11/nf-d3d11-id3d11device-setprivatedatainterface>)

# ID3D11Device::SetPrivateDataInterface


## -description

Associate an IUnknown-derived interface with this device child and associate that interface with an application-defined guid.

## -parameters

### -param guid [in]

Type: <b><a href="/openspecs/windows_protocols/ms-oaut/6e7d7108-c213-40bc-8294-ac13fe68fd50">REFGUID</a></b>

Guid associated with the interface.

### -param pData [in, optional]

Type: <b>const IUnknown*</b>

A pointer to the [IUnknown](/windows/win32/api/unknwn/nn-unknwn-iunknown)-derived interface to be associated with the device object. Its reference count is incremented when set, and decremented when either the [ID3D11Device](./nn-d3d11-id3d11device-6e49ef4b9e.md) is destroyed, or when the data is overwritten by calling [SetPrivateData](./nf-d3d11-id3d11device-setprivatedata-701bc6188e.md) or **SetPrivateDataInterface** with the same **GUID**.

## -returns

Type: <b><a href="/windows/win32/com/structure-of-com-error-codes">HRESULT</a></b>

This method returns one of the following <a href="/windows/desktop/direct3d11/d3d11-graphics-reference-returnvalues">Direct3D 11 Return Codes</a>.

## -see-also

<a href="/windows/desktop/api/d3d11/nn-d3d11-id3d11device">ID3D11Device</a>