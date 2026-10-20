Source: [https://learn.microsoft.com/en-us/windows/win32/api/D3D11/nf-d3d11-id3d11device-getexceptionmode](<https://learn.microsoft.com/en-us/windows/win32/api/D3D11/nf-d3d11-id3d11device-getexceptionmode>)

# ID3D11Device::GetExceptionMode


## -description

Get the exception-mode flags.



## -returns

Type: <b><a href="/windows/desktop/WinProg/windows-data-types">UINT</a></b>

A value that contains one or more exception flags; each flag specifies a condition which will cause an exception to be raised. The flags are listed in <a href="/windows/desktop/api/d3d11/ne-d3d11-d3d11_raise_flag">D3D11_RAISE_FLAG</a>. A default value of 0 means there are no flags.

## -remarks

An exception-mode flag is used to elevate an error condition to a non-continuable exception.

## -see-also

<a href="/windows/desktop/api/d3d11/nn-d3d11-id3d11device">ID3D11Device</a>