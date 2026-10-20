Source: [https://learn.microsoft.com/en-us/windows/win32/api/D3D11/nf-d3d11-id3d11device-setprivatedata](<https://learn.microsoft.com/en-us/windows/win32/api/D3D11/nf-d3d11-id3d11device-setprivatedata>)

# ID3D11Device::SetPrivateData


## -description

Set data to a device and associate that data with a guid.

## -parameters

### -param guid [in]

Type: <b><a href="/openspecs/windows_protocols/ms-oaut/6e7d7108-c213-40bc-8294-ac13fe68fd50">REFGUID</a></b>

Guid associated with the data.

### -param DataSize [in]

Type: <b><a href="/windows/desktop/WinProg/windows-data-types">UINT</a></b>

Size of the data.

### -param pData [in, optional]

Type: <b>const void*</b>

Pointer to the data to be stored with this device. If pData is <b>NULL</b>, DataSize must also be 0, and any data previously associated with the guid will be destroyed.

## -returns

Type: <b><a href="/windows/win32/com/structure-of-com-error-codes">HRESULT</a></b>

This method returns one of the following <a href="/windows/desktop/direct3d11/d3d11-graphics-reference-returnvalues">Direct3D 11 Return Codes</a>.

## -remarks

The data stored in the device with this method can be retrieved with <a href="/windows/desktop/api/d3d11/nf-d3d11-id3d11device-getprivatedata">ID3D11Device::GetPrivateData</a>.

The data and guid set with this method will typically be application-defined.

The <a href="/windows/desktop/direct3d11/overviews-direct3d-11-devices-layers">debug layer</a> reports memory leaks by outputting a list of object interface pointers along with their friendly names. The default friendly name is "&lt;unnamed&gt;". You can set the friendly name so that you can determine if the corresponding object interface pointer caused the leak. To set the friendly name, use the <b>SetPrivateData</b> method and the <b>WKPDID_D3DDebugObjectName</b> GUID that is in D3Dcommon.h. For example, to give pContext a friendly name of <i>My name</i>, use the following code:


```

static const char c_szName[] = "My name";
hr = pContext->SetPrivateData( WKPDID_D3DDebugObjectName, sizeof( c_szName ) - 1, c_szName );

```

## -see-also

<a href="/windows/desktop/api/d3d11/nn-d3d11-id3d11device">ID3D11Device</a>