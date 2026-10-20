Source: [https://learn.microsoft.com/en-us/windows/win32/api/D3D11ShaderTracing/ns-d3d11shadertracing-d3d11_trace_value](<https://learn.microsoft.com/en-us/windows/win32/api/D3D11ShaderTracing/ns-d3d11shadertracing-d3d11_trace_value>)

# D3D11_TRACE_VALUE structure


## -description

Describes a trace value.

## -struct-fields

### -field Bits

An array of bits that make up the trace value. The [0] element is X.
            

<div class="alert"><b>Note</b>  This member can hold <b>float</b>, <b>UINT</b>, or <b>INT</b> data.
              The elements are specified as <b>UINT</b> rather than using a union to minimize the risk of x86 SNaN-&gt;QNaN quashing during float assignment.
              If the bits are displayed, they can be interpreted as <b>float</b> at the last moment.
            </div>
<div> </div>

### -field ValidMask

A combination of the following component values that are combined by using a bitwise <b>OR</b> operation.
            The resulting value specifies the component trace mask.
            

<table>
<tr>
<th>Flag</th>
<th>Description</th>
</tr>
<tr>
<td>D3D11_TRACE_COMPONENT_X (0x1)</td>
<td>The x component of the trace mask.</td>
</tr>
<tr>
<td>D3D11_TRACE_COMPONENT_Y (0x2)</td>
<td>The y component of the trace mask.</td>
</tr>
<tr>
<td>D3D11_TRACE_COMPONENT_Z (0x4)</td>
<td>The depth z component of the trace mask.</td>
</tr>
<tr>
<td>D3D11_TRACE_COMPONENT_W (0x8)</td>
<td>The depth w component of the trace mask.</td>
</tr>
</table>
 

Ignore unmasked values, particularly if deltas are accumulated.

## -remarks

This API requires the Windows Software Development Kit (SDK) for Windows 8.

## -see-also

<a href="/windows/desktop/direct3d11/d3d11-graphics-reference-shader-structures">Shader Structures</a>