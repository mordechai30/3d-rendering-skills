Source: [https://learn.microsoft.com/en-us/windows/win32/api/D3D11Shader/ns-d3d11shader-d3d11_shader_buffer_desc](<https://learn.microsoft.com/en-us/windows/win32/api/D3D11Shader/ns-d3d11shader-d3d11_shader_buffer_desc>)

# D3D11_SHADER_BUFFER_DESC structure


## -description

Describes a shader constant-buffer.

## -struct-fields

### -field Name

Type: <b><a href="/windows/desktop/WinProg/windows-data-types">LPCSTR</a></b>

The name of the buffer.

### -field Type

Type: <b><a href="/windows/desktop/api/d3dcommon/ne-d3dcommon-d3d_cbuffer_type">D3D_CBUFFER_TYPE</a></b>

A <a href="/windows/desktop/api/d3dcommon/ne-d3dcommon-d3d_cbuffer_type">D3D_CBUFFER_TYPE</a>-typed value that indicates the intended use of the constant data.

### -field Variables

Type: <b><a href="/windows/desktop/WinProg/windows-data-types">UINT</a></b>

The number of unique variables.

### -field Size

Type: <b><a href="/windows/desktop/WinProg/windows-data-types">UINT</a></b>

Buffer size (in bytes).

### -field uFlags

Type: <b><a href="/windows/desktop/WinProg/windows-data-types">UINT</a></b>

A combination of <a href="/windows/desktop/api/d3dcommon/ne-d3dcommon-d3d_shader_cbuffer_flags">D3D_SHADER_CBUFFER_FLAGS</a>-typed values that are combined by using a bitwise OR operation. The resulting value specifies properties for the shader constant-buffer.

## -remarks

Constants are supplied to shaders in a shader-constant buffer. Get the description of a shader-constant-buffer by calling <a href="/windows/desktop/api/d3d11shader/nf-d3d11shader-id3d11shaderreflectionconstantbuffer-getdesc">ID3D11ShaderReflectionConstantBuffer::GetDesc</a>.

## -see-also

<a href="/windows/desktop/direct3d11/d3d11-graphics-reference-shader-structures">Shader Structures</a>