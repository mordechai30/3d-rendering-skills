Source: [https://learn.microsoft.com/en-us/windows/win32/api/d3dcommon/ne-d3dcommon-d3d_resource_return_type](<https://learn.microsoft.com/en-us/windows/win32/api/d3dcommon/ne-d3dcommon-d3d_resource_return_type>)

# D3D_RESOURCE_RETURN_TYPE enumeration


## -description

Indicates return value type.

> [!NOTE]
> For programming with Direct3D 10, this API has a type alias that begins `D3D10_` instead of `D3D_`. These Direct3D 10 type aliases are defined in `d3d10.h`, `d3d10misc.h`, and `d3d10shader.h`.

## -enum-fields

### -field D3D_RETURN_TYPE_UNORM:1

### -field D3D_RETURN_TYPE_SNORM:2

### -field D3D_RETURN_TYPE_SINT:3

### -field D3D_RETURN_TYPE_UINT:4

### -field D3D_RETURN_TYPE_FLOAT:5

### -field D3D_RETURN_TYPE_MIXED:6

### -field D3D_RETURN_TYPE_DOUBLE:7

### -field D3D_RETURN_TYPE_CONTINUED:8

### -field D3D10_RETURN_TYPE_UNORM

### -field D3D10_RETURN_TYPE_SNORM

### -field D3D10_RETURN_TYPE_SINT

### -field D3D10_RETURN_TYPE_UINT

### -field D3D10_RETURN_TYPE_FLOAT

### -field D3D10_RETURN_TYPE_MIXED

### -field D3D11_RETURN_TYPE_UNORM

Return type is UNORM.

### -field D3D11_RETURN_TYPE_SNORM

Return type is SNORM.

### -field D3D11_RETURN_TYPE_SINT

Return type is SINT.

### -field D3D11_RETURN_TYPE_UINT

Return type is UINT.

### -field D3D11_RETURN_TYPE_FLOAT

Return type is FLOAT.

### -field D3D11_RETURN_TYPE_MIXED

Return type is unknown.

### -field D3D11_RETURN_TYPE_DOUBLE

Return type is DOUBLE.

### -field D3D11_RETURN_TYPE_CONTINUED

Return type is a multiple-dword type, such as a double or uint64, and the component is continued from the previous component that was declared.  The first component represents the lower bits.

## -remarks

The    <b>D3D11_RESOURCE_RETURN_TYPE</b> enumeration is type defined in the  D3D11shader.h header file as a <a href="/windows/desktop/api/d3dcommon/ne-d3dcommon-d3d_resource_return_type">D3D_RESOURCE_RETURN_TYPE</a> enumeration, which is fully defined in the  D3DCommon.h header file.


```

typedef D3D_RESOURCE_RETURN_TYPE D3D11_RESOURCE_RETURN_TYPE;
```

## -see-also

<a href="/windows/desktop/direct3d11/d3d11-graphics-reference-shader-enums">Shader Enumerations</a>