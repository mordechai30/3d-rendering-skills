Source: [https://learn.microsoft.com/en-us/windows/win32/api/d3dcommon/ne-d3dcommon-d3d_parameter_flags](<https://learn.microsoft.com/en-us/windows/win32/api/d3dcommon/ne-d3dcommon-d3d_parameter_flags>)

# D3D_PARAMETER_FLAGS enumeration


## -description

Indicates semantic flags for function parameters.

## -enum-fields

### -field D3D_PF_NONE:0

The parameter has no semantic flags.

### -field D3D_PF_IN:0x1

Indicates an input parameter.

### -field D3D_PF_OUT:0x2

Indicates an output parameter.

### -field D3D_PF_FORCE_DWORD:0x7fffffff

Forces this enumeration to compile to 32 bits in size. Without this value, some compilers would allow this enumeration to compile to a size other than 32 bits. This value is not used.

## -see-also

<a href="/windows/desktop/api/d3d11shader/ns-d3d11shader-d3d11_parameter_desc">D3D11_PARAMETER_DESC</a>



<a href="/windows/desktop/direct3d11/d3d11-graphics-reference-shader-enums">Shader Enumerations</a>