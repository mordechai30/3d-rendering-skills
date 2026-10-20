Source: [https://learn.microsoft.com/en-us/windows/win32/api/d3dcommon/ne-d3dcommon-d3d_tessellator_domain](<https://learn.microsoft.com/en-us/windows/win32/api/d3dcommon/ne-d3dcommon-d3d_tessellator_domain>)

# D3D_TESSELLATOR_DOMAIN enumeration


## -description

Domain options for tessellator data.

## -enum-fields

### -field D3D_TESSELLATOR_DOMAIN_UNDEFINED:0

### -field D3D_TESSELLATOR_DOMAIN_ISOLINE:1

### -field D3D_TESSELLATOR_DOMAIN_TRI:2

### -field D3D_TESSELLATOR_DOMAIN_QUAD:3

### -field D3D11_TESSELLATOR_DOMAIN_UNDEFINED

The data type is undefined.

### -field D3D11_TESSELLATOR_DOMAIN_ISOLINE

Isoline data.

### -field D3D11_TESSELLATOR_DOMAIN_TRI

Triangle data.

### -field D3D11_TESSELLATOR_DOMAIN_QUAD

Quad data.

## -remarks

The data domain defines the type of data. This enumeration is used by <a href="/windows/desktop/api/d3d11shader/ns-d3d11shader-d3d11_shader_desc">D3D11_SHADER_DESC</a>.

The <b>D3D11_TESSELLATOR_DOMAIN</b>     enumeration is type defined in the  D3D11Shader.h header file as a <a href="/windows/desktop/api/d3dcommon/ne-d3dcommon-d3d_tessellator_domain">D3D_TESSELLATOR_DOMAIN</a> enumeration, which is fully defined in the  D3DCommon.h header file.


```

typedef D3D_TESSELLATOR_DOMAIN D3D11_TESSELLATOR_DOMAIN;
```

## -see-also

<a href="/windows/desktop/direct3d11/d3d11-graphics-reference-shader-enums">Shader Enumerations</a>