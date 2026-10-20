Source: [https://learn.microsoft.com/en-us/windows/win32/api/d3dcommon/ne-d3dcommon-d3d_min_precision](<https://learn.microsoft.com/en-us/windows/win32/api/d3dcommon/ne-d3dcommon-d3d_min_precision>)

# D3D_MIN_PRECISION enumeration


## -description

Values that indicate the minimum desired interpolation precision.

## -enum-fields

### -field D3D_MIN_PRECISION_DEFAULT:0

Default minimum precision, which is 32-bit precision.

### -field D3D_MIN_PRECISION_FLOAT_16:1

Minimum precision is min16float, which is 16-bit floating point.

### -field D3D_MIN_PRECISION_FLOAT_2_8:2

Minimum precision is min10float, which is 10-bit floating point.

### -field D3D_MIN_PRECISION_RESERVED:3

Reserved

### -field D3D_MIN_PRECISION_SINT_16:4

Minimum precision is min16int, which is 16-bit signed integer.

### -field D3D_MIN_PRECISION_UINT_16:5

Minimum precision is min16uint, which is 16-bit unsigned integer.

### -field D3D_MIN_PRECISION_ANY_16:0xf0

Minimum precision is any 16-bit value.

### -field D3D_MIN_PRECISION_ANY_10:0xf1

Minimum precision is any 10-bit value.

## -remarks

For more info, see <a href="/windows/desktop/direct3dhlsl/dx-graphics-hlsl-scalar">Scalar Types</a> and <a href="/windows/desktop/direct3dhlsl/using-hlsl-minimum-precision">Using HLSL minimum precision</a>.

## -see-also

<a href="/windows/desktop/direct3d11/d3d11-graphics-reference-d3d11-common-enumerations">Common Version Enumerations</a>