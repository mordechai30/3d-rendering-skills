Source: [https://learn.microsoft.com/en-us/windows/win32/api/D3D11/ne-d3d11-d3d11_async_getdata_flag](<https://learn.microsoft.com/en-us/windows/win32/api/D3D11/ne-d3d11-d3d11_async_getdata_flag>)

# D3D11_ASYNC_GETDATA_FLAG enumeration


## -description

Optional flags that control the behavior of <a href="/windows/desktop/api/d3d11/nf-d3d11-id3d11devicecontext-getdata">ID3D11DeviceContext::GetData</a>.

## -enum-fields

### -field D3D11_ASYNC_GETDATA_DONOTFLUSH:0x1

Do not flush the command buffer. This can potentially cause an infinite loop if GetData is continually called until it returns S_OK as there may still be commands in the command buffer that need to be processed in order for GetData to return S_OK. Since the commands in the command buffer are not flushed they will not be processed and therefore GetData will never return S_OK.

## -see-also

<a href="/windows/desktop/direct3d11/d3d11-graphics-reference-d3d11-core-enums">Core Enumerations</a>