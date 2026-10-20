Source: [https://learn.microsoft.com/en-us/windows/win32/api/D3D11Shader/ns-d3d11shader-d3d11_shader_type_desc](<https://learn.microsoft.com/en-us/windows/win32/api/D3D11Shader/ns-d3d11shader-d3d11_shader_type_desc>)

# D3D11_SHADER_TYPE_DESC structure


## -description

Describes a shader-variable type.

## -struct-fields

### -field Class

Type: <b><a href="/windows/desktop/api/d3dcommon/ne-d3dcommon-d3d_shader_variable_class">D3D_SHADER_VARIABLE_CLASS</a></b>

A <a href="/windows/desktop/api/d3dcommon/ne-d3dcommon-d3d_shader_variable_class">D3D_SHADER_VARIABLE_CLASS</a>-typed value that identifies the variable class as one of scalar, vector, matrix, object, and so on.

### -field Type

Type: <b><a href="/windows/desktop/api/d3dcommon/ne-d3dcommon-d3d_shader_variable_type">D3D_SHADER_VARIABLE_TYPE</a></b>

A <a href="/windows/desktop/api/d3dcommon/ne-d3dcommon-d3d_shader_variable_type">D3D_SHADER_VARIABLE_TYPE</a>-typed value that identifies the variable type.

### -field Rows

Type: <b><a href="/windows/desktop/WinProg/windows-data-types">UINT</a></b>

Number of rows in a matrix. Otherwise a numeric type returns 1, any other type returns 0.

### -field Columns

Type: <b><a href="/windows/desktop/WinProg/windows-data-types">UINT</a></b>

Number of columns in a matrix. Otherwise a numeric type returns 1, any other type returns 0.

### -field Elements

Type: <b><a href="/windows/desktop/WinProg/windows-data-types">UINT</a></b>

Number of elements in an array; otherwise 0.

### -field Members

Type: <b><a href="/windows/desktop/WinProg/windows-data-types">UINT</a></b>

Number of members in the structure; otherwise 0.

### -field Offset

Type: <b><a href="/windows/desktop/WinProg/windows-data-types">UINT</a></b>

Offset, in bytes, between the start of the parent structure and this variable. Can be 0 if not a structure member.

### -field Name

Type: <b><a href="/windows/desktop/WinProg/windows-data-types">LPCSTR</a></b>

Name of the shader-variable type. This member can be <b>NULL</b> if it isn't used. This member supports dynamic shader linkage interface types, which have names. For more info about dynamic shader linkage, see <a href="/windows/desktop/direct3dhlsl/overviews-direct3d-11-hlsl-dynamic-linking">Dynamic Linking</a>.

## -remarks

Get a shader-variable-type description by calling <a href="/windows/desktop/api/d3d11shader/nf-d3d11shader-id3d11shaderreflectiontype-getdesc">ID3D11ShaderReflectionType::GetDesc</a>.

## -see-also

<a href="/windows/desktop/direct3d11/d3d11-graphics-reference-shader-structures">Shader Structures</a>