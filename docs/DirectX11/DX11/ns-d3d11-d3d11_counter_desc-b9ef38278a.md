Source: [https://learn.microsoft.com/en-us/windows/win32/api/D3D11/ns-d3d11-d3d11_counter_desc](<https://learn.microsoft.com/en-us/windows/win32/api/D3D11/ns-d3d11-d3d11_counter_desc>)

# D3D11_COUNTER_DESC structure


## -description

Describes a counter.

## -struct-fields

### -field Counter

Type: <b><a href="/windows/desktop/api/d3d11/ne-d3d11-d3d11_counter">D3D11_COUNTER</a></b>

Type of counter (see <a href="/windows/desktop/api/d3d11/ne-d3d11-d3d11_counter">D3D11_COUNTER</a>).

### -field MiscFlags

Type: <b><a href="/windows/desktop/WinProg/windows-data-types">UINT</a></b>

Reserved.

## -remarks

This structure is used by <a href="/windows/desktop/api/d3d11/nf-d3d11-id3d11counter-getdesc">ID3D11Counter::GetDesc</a>, <a href="/windows/desktop/api/d3d11/nf-d3d11-id3d11device-checkcounter">ID3D11Device::CheckCounter</a> and <a href="/windows/desktop/api/d3d11/nf-d3d11-id3d11device-createcounter">ID3D11Device::CreateCounter</a>.

## -see-also

<a href="/windows/desktop/direct3d11/d3d11-graphics-reference-d3d11-core-structures">Core Structures</a>