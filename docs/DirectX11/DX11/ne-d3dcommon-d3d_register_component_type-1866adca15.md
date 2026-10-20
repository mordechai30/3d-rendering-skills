Source: [https://learn.microsoft.com/en-us/windows/win32/api/d3dcommon/ne-d3dcommon-d3d_register_component_type](<https://learn.microsoft.com/en-us/windows/win32/api/d3dcommon/ne-d3dcommon-d3d_register_component_type>)

# D3D_REGISTER_COMPONENT_TYPE enumeration


## -description

Values that identify the data types that can be stored in a register.

> [!NOTE]
> For programming with Direct3D 10, this API has a type alias that begins `D3D10_` instead of `D3D_`. These Direct3D 10 type aliases are defined in `d3d10.h`, `d3d10misc.h`, and `d3d10shader.h`.

## -enum-fields

### -field D3D_REGISTER_COMPONENT_UNKNOWN:0

The data type is unknown.

### -field D3D_REGISTER_COMPONENT_UINT32:1

32-bit unsigned integer.

### -field D3D_REGISTER_COMPONENT_SINT32:2

32-bit signed integer.

### -field D3D_REGISTER_COMPONENT_FLOAT32:3

32-bit floating-point number.

### -field D3D10_REGISTER_COMPONENT_UNKNOWN

The data type is unknown.

### -field D3D10_REGISTER_COMPONENT_UINT32

32-bit unsigned integer.

### -field D3D10_REGISTER_COMPONENT_SINT32

32-bit signed integer.

### -field D3D10_REGISTER_COMPONENT_FLOAT32

32-bit floating-point number.

## -remarks

A register component type is specified in the <b>ComponentType</b> member of the <a href="/windows/win32/api/d3d11shader/ns-d3d11shader-d3d11_signature_parameter_desc">D3D11_SIGNATURE_PARAMETER_DESC</a> structure.

## -see-also

<a href="/windows/desktop/direct3d11/d3d11-graphics-reference-d3d11-common-enumerations">Common Version Enumerations</a>