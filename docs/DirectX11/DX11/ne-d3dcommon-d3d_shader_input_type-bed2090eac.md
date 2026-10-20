Source: [https://learn.microsoft.com/en-us/windows/win32/api/d3dcommon/ne-d3dcommon-d3d_shader_input_type](<https://learn.microsoft.com/en-us/windows/win32/api/d3dcommon/ne-d3dcommon-d3d_shader_input_type>)

# D3D_SHADER_INPUT_TYPE enumeration


## -description

Values that identify resource types that can be bound to a shader and that are reflected as part of the resource description for the shader.

> [!NOTE]
> For programming with Direct3D 10, this API has a type alias that begins `D3D10_` instead of `D3D_`. These Direct3D 10 type aliases are defined in `d3d10.h`, `d3d10misc.h`, and `d3d10shader.h`.

## -enum-fields

### -field D3D_SIT_CBUFFER:0

The shader resource is a constant buffer.

### -field D3D_SIT_TBUFFER

The shader resource is a texture buffer.

### -field D3D_SIT_TEXTURE

The shader resource is a texture.

### -field D3D_SIT_SAMPLER

The shader resource is a sampler.

### -field D3D_SIT_UAV_RWTYPED

The shader resource is a read-and-write buffer or texture.

### -field D3D_SIT_STRUCTURED

The shader resource is a structured buffer.

For more information about structured buffer, see the <b>Remarks</b> section.

### -field D3D_SIT_UAV_RWSTRUCTURED

The shader resource is a read-and-write structured buffer.

### -field D3D_SIT_BYTEADDRESS

The shader resource is a byte-address buffer.

### -field D3D_SIT_UAV_RWBYTEADDRESS

The shader resource is a read-and-write byte-address buffer.

### -field D3D_SIT_UAV_APPEND_STRUCTURED

The shader resource is an append-structured buffer.

### -field D3D_SIT_UAV_CONSUME_STRUCTURED

The shader resource is a consume-structured buffer.

### -field D3D_SIT_UAV_RWSTRUCTURED_WITH_COUNTER

The shader resource is a read-and-write structured buffer that uses the built-in counter to append or consume.

### -field D3D10_SIT_CBUFFER

The shader resource is a constant buffer.

### -field D3D10_SIT_TBUFFER

The shader resource is a texture buffer.

### -field D3D10_SIT_TEXTURE

The shader resource is a texture.

### -field D3D10_SIT_SAMPLER

The shader resource is a sampler.

### -field D3D11_SIT_UAV_RWTYPED

The shader resource is a read-and-write buffer.

### -field D3D11_SIT_STRUCTURED

The shader resource is a structured buffer.

For more information about structured buffer, see the <b>Remarks</b> section.

### -field D3D11_SIT_UAV_RWSTRUCTURED

The shader resource is a read-and-write structured buffer.

### -field D3D11_SIT_BYTEADDRESS

The shader resource is a byte-address buffer.

### -field D3D11_SIT_UAV_RWBYTEADDRESS

The shader resource is a read-and-write byte-address buffer.

### -field D3D11_SIT_UAV_APPEND_STRUCTURED

The shader resource is an append-structured buffer.

### -field D3D11_SIT_UAV_CONSUME_STRUCTURED

The shader resource is a consume-structured buffer.

### -field D3D11_SIT_UAV_RWSTRUCTURED_WITH_COUNTER

The shader resource is a read-and-write structured buffer that uses the built-in counter to append or consume.

## -remarks

<b>D3D_SHADER_INPUT_TYPE</b>-typed values are specified in the <b>Type</b> member of the <a href="/windows/win32/api/d3d11shader/ns-d3d11shader-d3d11_shader_input_bind_desc">D3D11_SHADER_INPUT_BIND_DESC</a> structure.

## -see-also

<a href="/windows/desktop/direct3d11/d3d11-graphics-reference-d3d11-common-enumerations">Common Version Enumerations</a>