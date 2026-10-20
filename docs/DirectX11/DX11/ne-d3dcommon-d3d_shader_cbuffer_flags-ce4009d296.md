Source: [https://learn.microsoft.com/en-us/windows/win32/api/d3dcommon/ne-d3dcommon-d3d_shader_cbuffer_flags](<https://learn.microsoft.com/en-us/windows/win32/api/d3dcommon/ne-d3dcommon-d3d_shader_cbuffer_flags>)

# D3D_SHADER_CBUFFER_FLAGS enumeration


## -description

Values that identify the intended use of a constant-data buffer.

> [!NOTE]
> For programming with Direct3D 10, this API has a type alias that begins `D3D10_` instead of `D3D_`. These Direct3D 10 type aliases are defined in `d3d10.h`, `d3d10misc.h`, and `d3d10shader.h`.

## -enum-fields

### -field D3D_CBF_USERPACKED:1

Bind the constant buffer to an input slot defined in HLSL code (instead of letting the compiler choose the input slot).

### -field D3D10_CBF_USERPACKED

Bind the constant buffer to an input slot defined in HLSL code (instead of letting the compiler choose the input slot).

### -field D3D_CBF_FORCE_DWORD:0x7fffffff

This value is not used by a programmer; it exists to force the enumeration to compile to 32 bits.

## -remarks

<b>D3D_SHADER_CBUFFER_FLAGS</b>-typed values are specified in the <b>uFlags</b> member of the <a href="/windows/desktop/api/d3d11shader/ns-d3d11shader-d3d11_shader_buffer_desc">D3D11_SHADER_BUFFER_DESC</a> structure.

## -see-also

<a href="/windows/desktop/direct3d11/d3d11-graphics-reference-d3d11-common-enumerations">Common Version Enumerations</a>