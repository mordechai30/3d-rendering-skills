Source: [https://learn.microsoft.com/en-us/windows/win32/api/D3D11/ns-d3d11-d3d11_input_element_desc](<https://learn.microsoft.com/en-us/windows/win32/api/D3D11/ns-d3d11-d3d11_input_element_desc>)

# D3D11_INPUT_ELEMENT_DESC structure


## -description

A description of a single element for the input-assembler stage.

## -struct-fields

### -field SemanticName

Type: <b><a href="/windows/desktop/WinProg/windows-data-types">LPCSTR</a></b>

The HLSL semantic associated with this element in a shader input-signature. See <a href="/windows/win32/direct3dhlsl/dx-graphics-hlsl-semantics">HLSL Semantics</a> for more info.

### -field SemanticIndex

Type: <b><a href="/windows/desktop/WinProg/windows-data-types">UINT</a></b>

The semantic index for the element. A semantic index modifies a semantic, with an integer index number. A semantic index is only needed in a
        case where there is more than one element with the same semantic. For example, a 4x4 matrix would have four components each with the semantic
        name


```
matrix
```


, however each of the four component would have different semantic indices (0, 1, 2, and 3).

### -field Format

Type: <b><a href="/windows/desktop/api/dxgiformat/ne-dxgiformat-dxgi_format">DXGI_FORMAT</a></b>

The data type of the element data. See <a href="/windows/desktop/api/dxgiformat/ne-dxgiformat-dxgi_format">DXGI_FORMAT</a>.

### -field InputSlot

Type: <b><a href="/windows/desktop/WinProg/windows-data-types">UINT</a></b>

An integer value that identifies the input-assembler (see input slot). Valid values are between 0 and 15, defined in D3D11.h.

### -field AlignedByteOffset

Type: <b><a href="/windows/desktop/WinProg/windows-data-types">UINT</a></b>

Optional. Offset (in bytes) from the start of the vertex. Use D3D11_APPEND_ALIGNED_ELEMENT for convenience to define the current element directly
        after the previous one, including any packing if necessary.

### -field InputSlotClass

Type: <b><a href="/windows/desktop/api/d3d11/ne-d3d11-d3d11_input_classification">D3D11_INPUT_CLASSIFICATION</a></b>

Identifies the input data class for a single input slot (see <a href="/windows/desktop/api/d3d11/ne-d3d11-d3d11_input_classification">D3D11_INPUT_CLASSIFICATION</a>).

### -field InstanceDataStepRate

Type: <b><a href="/windows/desktop/WinProg/windows-data-types">UINT</a></b>

The number of instances to draw using the same per-instance data before advancing in the buffer by one element. This value must be 0 for an
        element that contains per-vertex data (the slot class is set to D3D11_INPUT_PER_VERTEX_DATA).

## -remarks

An input-layout object contains an array of structures, each structure defines one element being read from an input slot. Create an input-layout
      object by calling <a href="/windows/desktop/api/d3d11/nf-d3d11-id3d11device-createinputlayout">ID3D11Device::CreateInputLayout</a>. For an example, see the "Create the Input-Layout Object" subtopic under the  <a href="/windows/desktop/direct3d11/d3d10-graphics-programming-guide-input-assembler-stage-getting-started">Getting Started with the Input-Assembler Stage</a> topic.

## -see-also

<a href="/windows/desktop/direct3d11/d3d11-graphics-reference-d3d11-core-structures">Core Structures</a>