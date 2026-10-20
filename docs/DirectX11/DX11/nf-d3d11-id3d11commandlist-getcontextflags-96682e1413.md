Source: [https://learn.microsoft.com/en-us/windows/win32/api/D3D11/nf-d3d11-id3d11commandlist-getcontextflags](<https://learn.microsoft.com/en-us/windows/win32/api/D3D11/nf-d3d11-id3d11commandlist-getcontextflags>)

# ID3D11CommandList::GetContextFlags


## -description

Gets the initialization flags associated with the deferred context that created the command list.



## -returns

Type: <b><a href="/windows/desktop/WinProg/windows-data-types">UINT</a></b>

The context flag is reserved for future use and is always 0.

## -remarks

The GetContextFlags method gets the flags that were supplied to the <i>ContextFlags</i> parameter of <a href="/windows/desktop/api/d3d11/nf-d3d11-id3d11device-createdeferredcontext">ID3D11Device::CreateDeferredContext</a>; however, the context flag is reserved for future use.

## -see-also

<a href="/windows/desktop/api/d3d11/nn-d3d11-id3d11commandlist">ID3D11CommandList</a>