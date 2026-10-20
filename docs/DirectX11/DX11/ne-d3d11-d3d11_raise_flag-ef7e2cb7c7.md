Source: [https://learn.microsoft.com/en-us/windows/win32/api/D3D11/ne-d3d11-d3d11_raise_flag](<https://learn.microsoft.com/en-us/windows/win32/api/D3D11/ne-d3d11-d3d11_raise_flag>)

# D3D11_RAISE_FLAG enumeration


## -description

Option(s) for raising an error to a non-continuable exception.

## -enum-fields

### -field D3D11_RAISE_FLAG_DRIVER_INTERNAL_ERROR:0x1L

Raise an internal driver error to a non-continuable exception.

## -remarks

These flags are used by <a href="/windows/desktop/api/d3d11/nf-d3d11-id3d11device-getexceptionmode">ID3D11Device::GetExceptionMode</a> and <a href="/windows/desktop/api/d3d11/nf-d3d11-id3d11device-setexceptionmode">ID3D11Device::SetExceptionMode</a>. Use 0 to indicate no flags; multiple flags can be logically OR'ed together.

## -see-also

<a href="/windows/desktop/direct3d11/d3d11-graphics-reference-d3d11-core-enums">Core Enumerations</a>