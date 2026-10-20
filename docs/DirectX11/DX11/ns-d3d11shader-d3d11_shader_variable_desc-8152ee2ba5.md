Source: [https://learn.microsoft.com/en-us/windows/win32/api/D3D11Shader/ns-d3d11shader-d3d11_shader_variable_desc](<https://learn.microsoft.com/en-us/windows/win32/api/D3D11Shader/ns-d3d11shader-d3d11_shader_variable_desc>)

# D3D11_SHADER_VARIABLE_DESC structure


## -description

Describes a shader variable.

## -struct-fields

### -field Name

Type: <b><a href="/windows/desktop/WinProg/windows-data-types">LPCSTR</a></b>

The variable name.

### -field StartOffset

Type: <b><a href="/windows/desktop/WinProg/windows-data-types">UINT</a></b>

Offset from the start of the parent structure to the beginning of the variable.

### -field Size

Type: <b><a href="/windows/desktop/WinProg/windows-data-types">UINT</a></b>

Size of the variable (in bytes).

### -field uFlags

Type: <b><a href="/windows/desktop/WinProg/windows-data-types">UINT</a></b>

A combination of <a href="/windows/desktop/api/d3dcommon/ne-d3dcommon-d3d_shader_variable_flags">D3D_SHADER_VARIABLE_FLAGS</a>-typed values that are combined by using a bitwise OR operation. The resulting value identifies shader-variable properties.

### -field DefaultValue

Type: <b><a href="/windows/desktop/WinProg/windows-data-types">LPVOID</a></b>

The default value for initializing the variable.

### -field StartTexture

Type: <b>UINT</b>

Offset from the start of the variable to the beginning of the texture.

### -field TextureSize

Type: <b>UINT</b>

The size of the texture, in bytes.

### -field StartSampler

Type: <b>UINT</b>

Offset from the start of the variable to the beginning of the sampler.

### -field SamplerSize

Type: <b>UINT</b>

The size of the sampler, in bytes.

## -remarks

Get a shader-variable description using reflection by calling <a href="/windows/desktop/api/d3d11shader/nf-d3d11shader-id3d11shaderreflectionvariable-getdesc">ID3D11ShaderReflectionVariable::GetDesc</a>.
        

As of the June 2010 update, <b>DefaultValue</b> emits default values for reflection.

## -see-also

<a href="/windows/desktop/direct3d11/d3d11-graphics-reference-shader-structures">Shader Structures</a>