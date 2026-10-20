Source: [https://learn.microsoft.com/en-us/windows/win32/api/D3D11/nf-d3d11-id3d11device-createcounter](<https://learn.microsoft.com/en-us/windows/win32/api/D3D11/nf-d3d11-id3d11device-createcounter>)

# ID3D11Device::CreateCounter


## -description

Create a counter object for measuring GPU performance.

## -parameters

### -param pCounterDesc [in]

Type: <b>const <a href="/windows/desktop/api/d3d11/ns-d3d11-d3d11_counter_desc">D3D11_COUNTER_DESC</a>*</b>

Pointer to a counter description (see <a href="/windows/desktop/api/d3d11/ns-d3d11-d3d11_counter_desc">D3D11_COUNTER_DESC</a>).

### -param ppCounter [out, optional]

Type: <b><a href="/windows/desktop/api/d3d11/nn-d3d11-id3d11counter">ID3D11Counter</a>**</b>

Address of a pointer to a counter (see <a href="/windows/desktop/api/d3d11/nn-d3d11-id3d11counter">ID3D11Counter</a>).

## -returns

Type: <b><a href="/windows/win32/com/structure-of-com-error-codes">HRESULT</a></b>

If this function succeeds, it will return S_OK. If it fails, possible return values are: S_FALSE, E_OUTOFMEMORY, DXGI_ERROR_UNSUPPORTED, DXGI_ERROR_NONEXCLUSIVE, or E_INVALIDARG.

DXGI_ERROR_UNSUPPORTED is returned whenever the application requests to create a well-known counter, but the current device does not support it.

DXGI_ERROR_NONEXCLUSIVE indicates that another device object is currently using the counters, so they cannot be used by this device at the moment.

E_INVALIDARG is returned whenever an out-of-range well-known or device-dependent counter is requested, or when the simulataneously active counters have been exhausted.

## -see-also

<a href="/windows/desktop/api/d3d11/nn-d3d11-id3d11device">ID3D11Device</a>