Source: [https://learn.microsoft.com/en-us/windows/win32/api/D3D11/ne-d3d11-d3d11_stencil_op](<https://learn.microsoft.com/en-us/windows/win32/api/D3D11/ne-d3d11-d3d11_stencil_op>)

# D3D11_STENCIL_OP enumeration


## -description

The stencil operations that can be performed during depth-stencil testing.

## -enum-fields

### -field D3D11_STENCIL_OP_KEEP:1

Keep the existing stencil data.

### -field D3D11_STENCIL_OP_ZERO:2

Set the stencil data to 0.

### -field D3D11_STENCIL_OP_REPLACE:3

Set the stencil data to the reference value set by calling <a href="/windows/desktop/api/d3d11/nf-d3d11-id3d11devicecontext-omsetdepthstencilstate">ID3D11DeviceContext::OMSetDepthStencilState</a>.

### -field D3D11_STENCIL_OP_INCR_SAT:4

Increment the stencil value by 1, and clamp the result.

### -field D3D11_STENCIL_OP_DECR_SAT:5

Decrement the stencil value by 1, and clamp the result.

### -field D3D11_STENCIL_OP_INVERT:6

Invert the stencil data.

### -field D3D11_STENCIL_OP_INCR:7

Increment the stencil value by 1, and wrap the result if necessary.

### -field D3D11_STENCIL_OP_DECR:8

Decrement the stencil value by 1, and wrap the result if necessary.

## -see-also

<a href="/windows/desktop/direct3d11/d3d11-graphics-reference-d3d11-core-enums">Core Enumerations</a>