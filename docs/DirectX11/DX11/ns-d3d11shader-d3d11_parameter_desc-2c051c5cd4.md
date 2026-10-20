Source: [https://learn.microsoft.com/en-us/windows/win32/api/D3D11Shader/ns-d3d11shader-d3d11_parameter_desc](<https://learn.microsoft.com/en-us/windows/win32/api/D3D11Shader/ns-d3d11shader-d3d11_parameter_desc>)

# D3D11_PARAMETER_DESC structure


## -description

Describes a function parameter.

## -struct-fields

### -field Name

Type: <b><a href="/windows/desktop/WinProg/windows-data-types">LPCSTR</a></b>

The name of the function parameter.

### -field SemanticName

Type: <b><a href="/windows/desktop/WinProg/windows-data-types">LPCSTR</a></b>

The HLSL <a href="/windows/desktop/direct3dhlsl/dx-graphics-hlsl-semantics">semantic</a> that is associated with this function parameter. This name includes the index, for example, SV_Target[n].

### -field Type

Type: <b><a href="/windows/desktop/api/d3dcommon/ne-d3dcommon-d3d_shader_variable_type">D3D_SHADER_VARIABLE_TYPE</a></b>

A <a href="/windows/desktop/api/d3dcommon/ne-d3dcommon-d3d_shader_variable_type">D3D_SHADER_VARIABLE_TYPE</a>-typed value that identifies the variable type for the parameter.

### -field Class

Type: <b><a href="/windows/desktop/api/d3dcommon/ne-d3dcommon-d3d_shader_variable_class">D3D_SHADER_VARIABLE_CLASS</a></b>

A <a href="/windows/desktop/api/d3dcommon/ne-d3dcommon-d3d_shader_variable_class">D3D_SHADER_VARIABLE_CLASS</a>-typed value that identifies the variable class for the parameter as one of scalar, vector, matrix, object, and so on.

### -field Rows

Type: <b><a href="/windows/desktop/WinProg/windows-data-types">UINT</a></b>

The number of rows for a matrix parameter.

### -field Columns

Type: <b><a href="/windows/desktop/WinProg/windows-data-types">UINT</a></b>

The number of columns for a matrix parameter.

### -field InterpolationMode

Type: <b><a href="/windows/desktop/api/d3dcommon/ne-d3dcommon-d3d_interpolation_mode">D3D_INTERPOLATION_MODE</a></b>

A <a href="/windows/desktop/api/d3dcommon/ne-d3dcommon-d3d_interpolation_mode">D3D_INTERPOLATION_MODE</a>-typed value that identifies the interpolation mode for the parameter.

### -field Flags

Type: <b><a href="/windows/desktop/api/d3dcommon/ne-d3dcommon-d3d_parameter_flags">D3D_PARAMETER_FLAGS</a></b>

A combination of <a href="/windows/desktop/api/d3dcommon/ne-d3dcommon-d3d_parameter_flags">D3D_PARAMETER_FLAGS</a>-typed values that are combined by using a bitwise OR operation. The resulting value specifies semantic flags for the parameter.

### -field FirstInRegister

Type: <b><a href="/windows/desktop/WinProg/windows-data-types">UINT</a></b>

The first input register for this parameter.

### -field FirstInComponent

Type: <b><a href="/windows/desktop/WinProg/windows-data-types">UINT</a></b>

The first input register component for this parameter.

### -field FirstOutRegister

Type: <b><a href="/windows/desktop/WinProg/windows-data-types">UINT</a></b>

The first output register for this parameter.

### -field FirstOutComponent

Type: <b><a href="/windows/desktop/WinProg/windows-data-types">UINT</a></b>

The first output register component for this parameter.

## -remarks

Get a function-parameter description by calling <a href="/windows/desktop/api/d3d11shader/nf-d3d11shader-id3d11functionparameterreflection-getdesc">ID3D11FunctionParameterReflection::GetDesc</a>.

## -see-also

<a href="/windows/desktop/api/d3d11shader/nf-d3d11shader-id3d11functionparameterreflection-getdesc">ID3D11FunctionParameterReflection::GetDesc</a>



<a href="/windows/desktop/direct3d11/d3d11-graphics-reference-shader-structures">Shader Structures</a>