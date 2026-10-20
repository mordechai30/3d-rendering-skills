Source: [https://learn.microsoft.com/en-us/windows/win32/api/d3dcommon/ne-d3dcommon-d3d_tessellator_partitioning](<https://learn.microsoft.com/en-us/windows/win32/api/d3dcommon/ne-d3dcommon-d3d_tessellator_partitioning>)

# D3D_TESSELLATOR_PARTITIONING enumeration


## -description

Partitioning options.

## -enum-fields

### -field D3D_TESSELLATOR_PARTITIONING_UNDEFINED:0

### -field D3D_TESSELLATOR_PARTITIONING_INTEGER:1

### -field D3D_TESSELLATOR_PARTITIONING_POW2:2

### -field D3D_TESSELLATOR_PARTITIONING_FRACTIONAL_ODD:3

### -field D3D_TESSELLATOR_PARTITIONING_FRACTIONAL_EVEN:4

### -field D3D11_TESSELLATOR_PARTITIONING_UNDEFINED

The partitioning type is undefined.

### -field D3D11_TESSELLATOR_PARTITIONING_INTEGER

Partition with integers only.

### -field D3D11_TESSELLATOR_PARTITIONING_POW2

Partition with a power-of-two number only.

### -field D3D11_TESSELLATOR_PARTITIONING_FRACTIONAL_ODD

Partition with an odd, fractional number.

### -field D3D11_TESSELLATOR_PARTITIONING_FRACTIONAL_EVEN

Partition with an even, fractional number.

## -remarks

During tessellation, the partition option helps to determine how the algorithm chooses the next partition value; this enumeration is used by <a href="/windows/desktop/api/d3d11shader/ns-d3d11shader-d3d11_shader_desc">D3D11_SHADER_DESC</a>.

The      <b>D3D11_TESSELLATOR_PARTITIONING</b> enumeration is type defined in the  D3D11Shader.h header file as a <a href="/windows/desktop/api/d3dcommon/ne-d3dcommon-d3d_tessellator_partitioning">D3D_TESSELLATOR_PARTITIONING</a> enumeration, which is fully defined in the  D3DCommon.h header file.


```

typedef D3D_TESSELLATOR_PARTITIONING D3D11_TESSELLATOR_PARTITIONING;
```

## -see-also

<a href="/windows/desktop/direct3d11/d3d11-graphics-reference-shader-enums">Shader Enumerations</a>