Source: [https://learn.microsoft.com/en-us/windows/win32/api/d3dcommon/ne-d3dcommon-d3d_name](<https://learn.microsoft.com/en-us/windows/win32/api/d3dcommon/ne-d3dcommon-d3d_name>)

# D3D_NAME enumeration


## -description

Values that identify shader parameters that use system-value semantics.

> [!NOTE]
> For programming with Direct3D 10, this API has a type alias that begins `D3D10_` instead of `D3D_`. These Direct3D 10 type aliases are defined in `d3d10.h`, `d3d10misc.h`, and `d3d10shader.h`.

## -enum-fields

### -field D3D_NAME_UNDEFINED:0

This parameter does not use a predefined system-value semantic.

### -field D3D_NAME_POSITION:1

This parameter contains position data.

### -field D3D_NAME_CLIP_DISTANCE:2

This parameter contains clip-distance data.

### -field D3D_NAME_CULL_DISTANCE:3

This parameter contains cull-distance data.

### -field D3D_NAME_RENDER_TARGET_ARRAY_INDEX:4

This parameter contains a render-target-array index.

### -field D3D_NAME_VIEWPORT_ARRAY_INDEX:5

This parameter contains a viewport-array index.

### -field D3D_NAME_VERTEX_ID:6

This parameter contains a vertex ID.

### -field D3D_NAME_PRIMITIVE_ID:7

This parameter contains a primitive ID.

### -field D3D_NAME_INSTANCE_ID:8

This parameter contains an instance ID.

### -field D3D_NAME_IS_FRONT_FACE:9

This parameter contains data that identifies whether or not the primitive faces the camera.

### -field D3D_NAME_SAMPLE_INDEX:10

This parameter contains a sampler-array index.

### -field D3D_NAME_FINAL_QUAD_EDGE_TESSFACTOR:11

This parameter contains one of four tessellation factors that correspond to the amount of parts that a quad patch is broken into along the given edge. This flag is used to tessellate a quad patch.

### -field D3D_NAME_FINAL_QUAD_INSIDE_TESSFACTOR:12

This parameter contains one of two tessellation factors that correspond to the amount of parts that a quad patch is broken into vertically and horizontally within the patch. This flag is used to tessellate a quad patch.

### -field D3D_NAME_FINAL_TRI_EDGE_TESSFACTOR:13

This parameter contains one of three tessellation factors that correspond to the amount of parts that a tri patch is broken into along the given edge. This flag is used to tessellate a tri patch.

### -field D3D_NAME_FINAL_TRI_INSIDE_TESSFACTOR:14

This parameter contains the tessellation factor that corresponds to the amount of parts that a tri patch is broken into within the patch. This flag is used to tessellate a tri patch.

### -field D3D_NAME_FINAL_LINE_DETAIL_TESSFACTOR:15

This parameter contains the tessellation factor that corresponds to the number of lines broken into within the patch. This flag is used to tessellate an isolines patch.

### -field D3D_NAME_FINAL_LINE_DENSITY_TESSFACTOR:16

This parameter contains the tessellation factor that corresponds to the number of lines that are created within the patch. This flag is used to tessellate an isolines patch.

### -field D3D_NAME_BARYCENTRICS:23

This parameter contains barycentric coordinate data.

### -field D3D_NAME_TARGET:64

This parameter contains render-target data.

### -field D3D_NAME_DEPTH:65

This parameter contains depth data.

### -field D3D_NAME_COVERAGE:66

This parameter contains alpha-coverage data.

### -field D3D_NAME_DEPTH_GREATER_EQUAL:67

This parameter signifies that the value is greater than or equal to a reference value. This flag is used to specify conservative depth for a pixel shader.

### -field D3D_NAME_DEPTH_LESS_EQUAL:68

This parameter signifies that the value is less than or equal to a reference value. This flag is used to specify conservative depth for a pixel shader.

### -field D3D_NAME_STENCIL_REF:69

This parameter contains a stencil reference.
            See <a href="/windows/desktop/direct3d11/shader-specified-stencil-reference-value">Shader Specified Stencil Reference Value</a>.

### -field D3D_NAME_INNER_COVERAGE:70

This parameter contains inner input coverage data.
            See <a href="/windows/desktop/direct3d11/conservative-rasterization">Conservative Rasterization</a>.

### -field D3D10_NAME_UNDEFINED

This parameter does not use a predefined system-value semantic.

### -field D3D10_NAME_POSITION

This parameter contains position data.

### -field D3D10_NAME_CLIP_DISTANCE

This parameter contains clip-distance data.

### -field D3D10_NAME_CULL_DISTANCE

This parameter contains cull-distance data.

### -field D3D10_NAME_RENDER_TARGET_ARRAY_INDEX

This parameter contains a render-target-array index.

### -field D3D10_NAME_VIEWPORT_ARRAY_INDEX

This parameter contains a viewport-array index.

### -field D3D10_NAME_VERTEX_ID

This parameter contains a vertex ID.

### -field D3D10_NAME_PRIMITIVE_ID

This parameter contains a primitive ID.

### -field D3D10_NAME_INSTANCE_ID

This parameter contains a instance ID.

### -field D3D10_NAME_IS_FRONT_FACE

This parameter contains data that identifies whether or not the primitive faces the camera.

### -field D3D10_NAME_SAMPLE_INDEX

This parameter contains a sampler-array index.

### -field D3D10_NAME_TARGET

This parameter contains render-target data.

### -field D3D10_NAME_DEPTH

This parameter contains depth data.

### -field D3D10_NAME_COVERAGE

This parameter contains alpha-coverage data.

### -field D3D11_NAME_FINAL_QUAD_EDGE_TESSFACTOR

This parameter contains one of four tessellation factors that correspond to the amount of parts that a quad patch is broken into along the given edge. This flag is used to tessellate a quad patch.

### -field D3D11_NAME_FINAL_QUAD_INSIDE_TESSFACTOR

This parameter contains one of two tessellation factors that correspond to the amount of parts that a quad patch is broken into vertically and horizontally within the patch. This flag is used to tessellate a quad patch.

### -field D3D11_NAME_FINAL_TRI_EDGE_TESSFACTOR

This parameter contains one of three tessellation factors that correspond to the amount of parts that a tri patch is broken into along the given edge. This flag is used to tessellate a tri patch.

### -field D3D11_NAME_FINAL_TRI_INSIDE_TESSFACTOR

This parameter contains the tessellation factor that corresponds to the amount of parts that a tri patch is broken into within the patch. This flag is used to tessellate a tri patch.

### -field D3D11_NAME_FINAL_LINE_DETAIL_TESSFACTOR

This parameter contains the tessellation factor that corresponds to the amount of lines broken into within the patch. This flag is used to tessellate an isolines patch.

### -field D3D11_NAME_FINAL_LINE_DENSITY_TESSFACTOR

This parameter contains the tessellation factor that corresponds to the amount of lines that are created within the patch. This flag is used to tessellate an isolines patch.

### -field D3D11_NAME_DEPTH_GREATER_EQUAL

This parameter signifies that the value is greater than or equal to a reference value. This flag is used to specify conservative depth for a pixel shader.

### -field D3D11_NAME_DEPTH_LESS_EQUAL

This parameter signifies that the value is less than or equal to a reference value. This flag is used to specify conservative depth for a pixel shader.

### -field D3D11_NAME_STENCIL_REF

This parameter contains a stencil reference.
            See <a href="/windows/desktop/direct3d11/shader-specified-stencil-reference-value">Shader Specified Stencil Reference Value</a>.

### -field D3D11_NAME_INNER_COVERAGE

This parameter contains inner input coverage data.
            See <a href="/windows/desktop/direct3d11/conservative-rasterization">Conservative Rasterization</a>.

### -field D3D12_NAME_BARYCENTRICS

This parameter contains barycentric coordinate data.

## -remarks

The <b>D3D_NAME</b> values identify shader parameters that have <a href="/windows/win32/api/d3d11shader/ns-d3d11shader-d3d11_signature_parameter_desc">predefined system-value</a> semantics. These values are used in a shader-signature description. For more information about shader-signature description, see <a href="/windows/desktop/api/d3d11shader/ns-d3d11shader-d3d11_signature_parameter_desc">D3D11_SIGNATURE_PARAMETER_DESC</a>.

## -see-also

<a href="/windows/desktop/direct3d11/d3d11-graphics-reference-d3d11-common-enumerations">Common Version Enumerations</a>



<a href="/windows/win32/api/d3d11shader/ns-d3d11shader-d3d11_signature_parameter_desc">D3D11_SIGNATURE_PARAMETER_DESC</a>