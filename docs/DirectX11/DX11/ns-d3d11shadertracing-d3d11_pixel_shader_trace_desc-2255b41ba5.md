Source: [https://learn.microsoft.com/en-us/windows/win32/api/D3D11ShaderTracing/ns-d3d11shadertracing-d3d11_pixel_shader_trace_desc](<https://learn.microsoft.com/en-us/windows/win32/api/D3D11ShaderTracing/ns-d3d11shadertracing-d3d11_pixel_shader_trace_desc>)

# D3D11_PIXEL_SHADER_TRACE_DESC structure


## -description

Describes an instance of a pixel shader to trace.

## -struct-fields

### -field Invocation

The invocation number of the instance of the pixel shader.

### -field X

The x-coordinate of the pixel.

### -field Y

The y-coordinate of the pixel.

### -field SampleMask

A value that describes a mask of pixel samples to trace. If this value specifies any of the masked samples, the trace is activated.  The least significant bit (LSB) is sample 0.  The non-multisample antialiasing (MSAA) counts as a sample count of 1; therefore, the LSB of <b>SampleMask</b> should be set. If set to zero, the pixel is not traced. However, pixel traces can still be enabled on an invocation basis.

## -remarks

This API requires the Windows Software Development Kit (SDK) for Windows 8.

## -see-also

<a href="/windows/desktop/direct3d11/d3d11-graphics-reference-shader-structures">Shader Structures</a>