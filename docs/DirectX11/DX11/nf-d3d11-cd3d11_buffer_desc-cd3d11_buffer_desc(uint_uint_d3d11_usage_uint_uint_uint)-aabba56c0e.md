Source: [https://learn.microsoft.com/en-us/windows/win32/api/d3d11/nf-d3d11-cd3d11_buffer_desc-cd3d11_buffer_desc(uint_uint_d3d11_usage_uint_uint_uint)](<https://learn.microsoft.com/en-us/windows/win32/api/d3d11/nf-d3d11-cd3d11_buffer_desc-cd3d11_buffer_desc(uint_uint_d3d11_usage_uint_uint_uint)>)

# CD3D11_BUFFER_DESC::CD3D11_BUFFER_DESC(UINT,UINT,D3D11_USAGE,UINT,UINT,UINT)


## -description

Instantiates a new instance of a <a href="/windows/desktop/api/d3d11/ns-d3d11-cd3d11_buffer_desc">CD3D11_BUFFER_DESC</a> structure that is initialized with <a href="/windows/desktop/api/d3d11/ns-d3d11-d3d11_buffer_desc">D3D11_BUFFER_DESC</a> values.

## -parameters

### -param byteWidth

Type: <b><a href="/windows/desktop/WinProg/windows-data-types">UINT</a></b>

Size of the buffer in bytes.

### -param bindFlags

Type: <b><a href="/windows/desktop/WinProg/windows-data-types">UINT</a></b>

A combination of <a href="/windows/desktop/api/d3d11/ne-d3d11-d3d11_bind_flag">D3D11_BIND_FLAG</a> values that are combined by using a bitwise OR operation. The resulting value identifies how the buffer will be bound to the pipeline.

### -param usage

Type: <b><a href="/windows/desktop/api/d3d11/ne-d3d11-d3d11_usage">D3D11_USAGE</a></b>

A <a href="/windows/desktop/api/d3d11/ne-d3d11-d3d11_usage">D3D11_USAGE</a>-typed value that identifies how the buffer is expected to be read from and written to. Frequency of update is a key factor.

### -param cpuaccessFlags

Type: <b><a href="/windows/desktop/WinProg/windows-data-types">UINT</a></b>

A combination of <a href="/windows/desktop/api/d3d11/ne-d3d11-d3d11_cpu_access_flag">D3D11_CPU_ACCESS_FLAG</a> values that are combined by using a bitwise OR operation or 0 if no CPU access is necessary. The resulting value identifies CPU access.

### -param miscFlags

Type: <b><a href="/windows/desktop/WinProg/windows-data-types">UINT</a></b>

A combination of <a href="/windows/desktop/api/d3d11/ne-d3d11-d3d11_resource_misc_flag">D3D11_RESOURCE_MISC_FLAG</a> values that are combined by using a bitwise OR operation or 0 if unused. The resulting value identifies miscellaneous buffer info.

### -param structureByteStride

Type: <b><a href="/windows/desktop/WinProg/windows-data-types">UINT</a></b>

The size of each element in the buffer structure (in bytes) when the buffer represents a structured buffer. For more info about structured buffers, see <a href="/windows/desktop/direct3d11/direct3d-11-advanced-stages-cs-resources">Structured Buffer</a>.

The size value in <i>structureByteStride</i> must match the size of the format that you use for views of the buffer. For example, if you use a shader resource view (SRV) to read a buffer in a pixel shader, the SRV format size must match the size value in <i>structureByteStride</i>.

## -see-also

<a href="/windows/desktop/api/d3d11/ns-d3d11-cd3d11_buffer_desc">CD3D11_BUFFER_DESC</a>