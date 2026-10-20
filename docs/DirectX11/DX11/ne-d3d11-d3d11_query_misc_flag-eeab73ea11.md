Source: [https://learn.microsoft.com/en-us/windows/win32/api/D3D11/ne-d3d11-d3d11_query_misc_flag](<https://learn.microsoft.com/en-us/windows/win32/api/D3D11/ne-d3d11-d3d11_query_misc_flag>)

# D3D11_QUERY_MISC_FLAG enumeration


## -description

Flags that describe miscellaneous query behavior.

## -enum-fields

### -field D3D11_QUERY_MISC_PREDICATEHINT:0x1

Tell the hardware that if it is not yet sure if something is hidden or not to draw it anyway. This is only used with an occlusion predicate. Predication data cannot be returned to your application via <a href="/windows/desktop/api/d3d11/nf-d3d11-id3d11devicecontext-getdata">ID3D11DeviceContext::GetData</a> when using this flag.

## -remarks

This flag is part of a query description (see <a href="/windows/desktop/api/d3d11/ns-d3d11-d3d11_query_desc">D3D11_QUERY_DESC</a>).

## -see-also

<a href="/windows/desktop/direct3d11/d3d11-graphics-reference-d3d11-core-enums">Core Enumerations</a>