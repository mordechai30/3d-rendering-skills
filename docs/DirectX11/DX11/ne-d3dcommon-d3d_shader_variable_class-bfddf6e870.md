Source: [https://learn.microsoft.com/en-us/windows/win32/api/d3dcommon/ne-d3dcommon-d3d_shader_variable_class](<https://learn.microsoft.com/en-us/windows/win32/api/d3dcommon/ne-d3dcommon-d3d_shader_variable_class>)

# D3D_SHADER_VARIABLE_CLASS enumeration


## -description

Values that identify the class of a shader variable.

> [!NOTE]
> For programming with Direct3D 10, this API has a type alias that begins `D3D10_` instead of `D3D_`. These Direct3D 10 type aliases are defined in `d3d10.h`, `d3d10misc.h`, and `d3d10shader.h`.

## -enum-fields

### -field D3D_SVC_SCALAR:0

The shader variable is a scalar.

### -field D3D_SVC_VECTOR

The shader variable is a vector.

### -field D3D_SVC_MATRIX_ROWS

The shader variable is a row-major matrix.

### -field D3D_SVC_MATRIX_COLUMNS

The shader variable is a column-major matrix.

### -field D3D_SVC_OBJECT

The shader variable is an object.

### -field D3D_SVC_STRUCT

The shader variable is a structure.

### -field D3D_SVC_INTERFACE_CLASS

The shader variable is a class.

### -field D3D_SVC_INTERFACE_POINTER

The shader variable is an interface.

### -field D3D10_SVC_SCALAR

The shader variable is a scalar.

### -field D3D10_SVC_VECTOR

The shader variable is a vector.

### -field D3D10_SVC_MATRIX_ROWS

The shader variable is a row-major matrix.

### -field D3D10_SVC_MATRIX_COLUMNS

The shader variable is a column-major matrix.

### -field D3D10_SVC_OBJECT

The shader variable is an object.

### -field D3D10_SVC_STRUCT

The shader variable is a structure.

### -field D3D11_SVC_INTERFACE_CLASS

The shader variable is a class.

### -field D3D11_SVC_INTERFACE_POINTER

The shader variable is an interface.

### -field D3D_SVC_FORCE_DWORD:0x7fffffff

This value is not used by a programmer; it exists to force the enumeration to compile to 32 bits.

## -remarks

The class of a shader variable is not a programming class; the class identifies the variable class such as scalar, vector, object, and so on. <b>D3D_SHADER_VARIABLE_CLASS</b>-typed values are specified in the <b>Class</b> member of the <a href="/windows/desktop/api/d3d11shader/ns-d3d11shader-d3d11_shader_type_desc">D3D11_SHADER_TYPE_DESC</a> structure.

## -see-also

<a href="/windows/desktop/direct3d11/d3d11-graphics-reference-d3d11-common-enumerations">Common Version Enumerations</a>