Source: [https://learn.microsoft.com/en-us/windows/win32/api/d3dcommon/ne-d3dcommon-d3d_interpolation_mode](<https://learn.microsoft.com/en-us/windows/win32/api/d3dcommon/ne-d3dcommon-d3d_interpolation_mode>)

# D3D_INTERPOLATION_MODE enumeration


## -description

Specifies interpolation mode, which affects how values are calculated during rasterization.

## -enum-fields

### -field D3D_INTERPOLATION_UNDEFINED:0

The interpolation mode is undefined.

### -field D3D_INTERPOLATION_CONSTANT:1

Don't interpolate between register values.

### -field D3D_INTERPOLATION_LINEAR:2

Interpolate linearly between register values.

### -field D3D_INTERPOLATION_LINEAR_CENTROID:3

Interpolate linearly between register values but centroid clamped when multisampling.

### -field D3D_INTERPOLATION_LINEAR_NOPERSPECTIVE:4

Interpolate linearly between register values but with no perspective correction.

### -field D3D_INTERPOLATION_LINEAR_NOPERSPECTIVE_CENTROID:5

Interpolate linearly between register values but with no perspective correction and centroid clamped when multisampling.

### -field D3D_INTERPOLATION_LINEAR_SAMPLE:6

Interpolate linearly between register values but sample clamped when multisampling.

### -field D3D_INTERPOLATION_LINEAR_NOPERSPECTIVE_SAMPLE:7

Interpolate linearly between register values but with no perspective correction and sample clamped when multisampling.

## -see-also

<a href="/windows/desktop/direct3d11/d3d11-graphics-reference-d3d11-common-enumerations">Common Version Enumerations</a>



<a href="/windows/desktop/api/d3d11shader/ns-d3d11shader-d3d11_parameter_desc">D3D11_PARAMETER_DESC</a>