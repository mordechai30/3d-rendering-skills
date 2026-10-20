Source: [https://learn.microsoft.com/en-us/windows/win32/api/D3D11SDKLayers/nf-d3d11sdklayers-id3d11debug-validatecontextfordispatch](<https://learn.microsoft.com/en-us/windows/win32/api/D3D11SDKLayers/nf-d3d11sdklayers-id3d11debug-validatecontextfordispatch>)

# ID3D11Debug::ValidateContextForDispatch


## -description

Verifies whether the dispatch pipeline state is valid.

## -parameters

### -param pContext [in]

Type: <b><a href="/windows/desktop/api/d3d11/nn-d3d11-id3d11devicecontext">ID3D11DeviceContext</a>*</b>

A pointer to the <a href="/windows/desktop/api/d3d11/nn-d3d11-id3d11devicecontext">ID3D11DeviceContext</a> that represents a device context.

## -returns

Type: <b><a href="/windows/win32/com/structure-of-com-error-codes">HRESULT</a></b>

This method returns one of the return codes described in the topic <a href="/windows/desktop/direct3d11/d3d11-graphics-reference-returnvalues">Direct3D 11 Return Codes</a>.

## -remarks

Use this method before you call a dispatch method (for example, <a href="/windows/desktop/api/d3d11/nf-d3d11-id3d11devicecontext-dispatch">ID3D11DeviceContext::Dispatch</a>). Validation requires the debug layer.

## -see-also

<a href="/windows/desktop/api/d3d11sdklayers/nn-d3d11sdklayers-id3d11debug">ID3D11Debug</a>