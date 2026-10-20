Source: [https://learn.microsoft.com/en-us/windows/win32/api/D3D11/nf-d3d11-id3d11device-checkformatsupport](<https://learn.microsoft.com/en-us/windows/win32/api/D3D11/nf-d3d11-id3d11device-checkformatsupport>)

# ID3D11Device::CheckFormatSupport


## -description

Get the support of a given format on the installed video device.

## -parameters

### -param Format [in]

Type: <b><a href="/windows/desktop/api/dxgiformat/ne-dxgiformat-dxgi_format">DXGI_FORMAT</a></b>

A <a href="/windows/desktop/api/dxgiformat/ne-dxgiformat-dxgi_format">DXGI_FORMAT</a> enumeration that describes a format for which to check for support.

### -param pFormatSupport [out]

Type: <b><a href="/windows/desktop/WinProg/windows-data-types">UINT</a>*</b>

A bitfield of <a href="/windows/desktop/api/d3d11/ne-d3d11-d3d11_format_support">D3D11_FORMAT_SUPPORT</a> enumeration values describing how the specified format is supported on the installed device. 
        The values are ORed together.

## -returns

Type: <b><a href="/windows/win32/com/structure-of-com-error-codes">HRESULT</a></b>

Returns S_OK if successful; otherwise, returns E_INVALIDARG if the <i>Format</i> parameter is <b>NULL</b>, or returns E_FAIL if the 
      described format does not exist.

## -see-also

<a href="/windows/desktop/api/d3d11/nn-d3d11-id3d11device">ID3D11Device</a>