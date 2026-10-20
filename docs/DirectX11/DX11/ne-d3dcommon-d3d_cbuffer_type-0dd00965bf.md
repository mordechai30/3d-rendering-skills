Source: [https://learn.microsoft.com/en-us/windows/win32/api/d3dcommon/ne-d3dcommon-d3d_cbuffer_type](<https://learn.microsoft.com/en-us/windows/win32/api/d3dcommon/ne-d3dcommon-d3d_cbuffer_type>)

## -description

Values that identify the intended use of constant-buffer data. 

> [!NOTE]
> For programming with Direct3D 10, this API has a type alias that begins `D3D10_` instead of `D3D_`. These Direct3D 10 type aliases are defined in `d3d10.h`, `d3d10misc.h`, and `d3d10shader.h`.

## -enum-fields

### -field D3D_CT_CBUFFER:0

A buffer containing scalar constants.

### -field D3D_CT_TBUFFER

A buffer containing texture data.

### -field D3D_CT_INTERFACE_POINTERS

A buffer containing interface pointers.

### -field D3D_CT_RESOURCE_BIND_INFO

A buffer containing binding information.

### -field D3D10_CT_CBUFFER

A buffer containing scalar constants.

### -field D3D10_CT_TBUFFER

A buffer containing texture data.

### -field D3D11_CT_CBUFFER

A buffer containing scalar constants.

### -field D3D11_CT_TBUFFER

A buffer containing texture data.

### -field D3D11_CT_INTERFACE_POINTERS

A buffer containing interface pointers.

### -field D3D11_CT_RESOURCE_BIND_INFO

A buffer containing binding information.

## -see-also

<a href="/windows/desktop/direct3d11/d3d11-graphics-reference-d3d11-common-enumerations">Common Version Enumerations</a>