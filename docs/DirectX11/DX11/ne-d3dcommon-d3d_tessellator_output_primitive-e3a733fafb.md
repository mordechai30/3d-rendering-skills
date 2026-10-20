Source: [https://learn.microsoft.com/en-us/windows/win32/api/d3dcommon/ne-d3dcommon-d3d_tessellator_output_primitive](<https://learn.microsoft.com/en-us/windows/win32/api/d3dcommon/ne-d3dcommon-d3d_tessellator_output_primitive>)

# D3D_TESSELLATOR_OUTPUT_PRIMITIVE enumeration


## -description

Output primitive types.

## -enum-fields

### -field D3D_TESSELLATOR_OUTPUT_UNDEFINED:0

### -field D3D_TESSELLATOR_OUTPUT_POINT:1

### -field D3D_TESSELLATOR_OUTPUT_LINE:2

### -field D3D_TESSELLATOR_OUTPUT_TRIANGLE_CW:3

### -field D3D_TESSELLATOR_OUTPUT_TRIANGLE_CCW:4

### -field D3D11_TESSELLATOR_OUTPUT_UNDEFINED

The output primitive type is undefined.

### -field D3D11_TESSELLATOR_OUTPUT_POINT

The output primitive type is a point.

### -field D3D11_TESSELLATOR_OUTPUT_LINE

The output primitive type is a line.

### -field D3D11_TESSELLATOR_OUTPUT_TRIANGLE_CW

The output primitive type is a clockwise triangle.

### -field D3D11_TESSELLATOR_OUTPUT_TRIANGLE_CCW

The output primitive type is a counter clockwise triangle.

## -remarks

The output primitive type determines how the tessellator output data is organized; this enumeration is used by <a href="/windows/desktop/api/d3d11shader/ns-d3d11shader-d3d11_shader_desc">D3D11_SHADER_DESC</a>.

The <b>D3D11_TESSELLATOR_OUTPUT_PRIMITIVE</b>     enumeration is type defined in the  D3D11Shader.h header file as a <a href="/windows/desktop/api/d3dcommon/ne-d3dcommon-d3d_tessellator_output_primitive">D3D_TESSELLATOR_OUTPUT_PRIMITIVE</a> enumeration, which is fully defined in the  D3DCommon.h header file.


```

typedef D3D_TESSELLATOR_OUTPUT_PRIMITIVE D3D11_TESSELLATOR_OUTPUT_PRIMITIVE;
```

## -see-also

<a href="/windows/desktop/direct3d11/d3d11-graphics-reference-shader-enums">Shader Enumerations</a>