Source: [https://learn.microsoft.com/en-us/windows/win32/api/D3D11_3/ne-d3d11_3-d3d11_context_type](<https://learn.microsoft.com/en-us/windows/win32/api/D3D11_3/ne-d3d11_3-d3d11_context_type>)

# D3D11_CONTEXT_TYPE enumeration


## -description

Specifies the context in which a query occurs.

## -enum-fields

### -field D3D11_CONTEXT_TYPE_ALL:0

The query can occur in all contexts.

### -field D3D11_CONTEXT_TYPE_3D:1

The query occurs in the context of a 3D command queue.

### -field D3D11_CONTEXT_TYPE_COMPUTE:2

The query occurs in the context of a 3D compute queue.

### -field D3D11_CONTEXT_TYPE_COPY:3

The query occurs in the context of a 3D copy queue.

### -field D3D11_CONTEXT_TYPE_VIDEO:4

The query occurs in the context of video.

## -remarks

This enum is used by the following:
        

<ul>
<li>
<a href="/windows/desktop/api/d3d11_3/ns-d3d11_3-cd3d11_query_desc1">D3D11_QUERY_DESC1</a> structure
          </li>
<li>A CD3D11_QUERY_DESC1 constructor.</li>
<li>
<a href="/windows/desktop/api/d3d11_3/nf-d3d11_3-id3d11devicecontext3-flush1">ID3D11DeviceContext3::Flush1</a> method
          </li>
</ul>

## -see-also

<a href="/windows/desktop/direct3d11/d3d11-graphics-reference-d3d11-core-enums">Core Enumerations</a>



<a href="/windows/desktop/api/d3d11_3/ns-d3d11_3-cd3d11_query_desc1">D3D11_QUERY_DESC1</a>