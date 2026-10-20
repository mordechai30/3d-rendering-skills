Source: [https://learn.microsoft.com/en-us/windows/win32/api/D3D11/nf-d3d11-id3d11devicecontext-iasetvertexbuffers](<https://learn.microsoft.com/en-us/windows/win32/api/D3D11/nf-d3d11-id3d11devicecontext-iasetvertexbuffers>)

# ID3D11DeviceContext::IASetVertexBuffers


## -description

Bind an array of vertex buffers to the <a href="/windows/desktop/direct3d11/d3d10-graphics-programming-guide-input-assembler-stage">input-assembler stage</a>.

## -parameters

### -param StartSlot [in]

Type: <b><a href="/windows/desktop/WinProg/windows-data-types">UINT</a></b>

The first input slot for binding. The first vertex buffer is explicitly bound to the start slot; this causes each additional vertex buffer in the array to be implicitly bound to each subsequent input slot. The maximum of 16 or 32 input slots (ranges from 0 to D3D11_IA_VERTEX_INPUT_RESOURCE_SLOT_COUNT - 1) are available; the <a href="/windows/desktop/direct3d11/overviews-direct3d-11-devices-downlevel-intro">maximum number of input slots depends on the feature level</a>.

### -param NumBuffers [in]

Type: <b><a href="/windows/desktop/WinProg/windows-data-types">UINT</a></b>

The number of vertex buffers in the array. The number of buffers (plus the starting slot) can't exceed the total number of IA-stage input slots (ranges from 0 to D3D11_IA_VERTEX_INPUT_RESOURCE_SLOT_COUNT - StartSlot).

### -param ppVertexBuffers [in, optional]

Type: <b><a href="/windows/desktop/api/d3d11/nn-d3d11-id3d11buffer">ID3D11Buffer</a>*</b>

A pointer to an array of vertex buffers (see <a href="/windows/desktop/api/d3d11/nn-d3d11-id3d11buffer">ID3D11Buffer</a>). The vertex buffers must have been created with the <a href="/windows/desktop/api/d3d11/ne-d3d11-d3d11_bind_flag">D3D11_BIND_VERTEX_BUFFER</a> flag.

### -param pStrides [in, optional]

Type: <b>const <a href="/windows/desktop/WinProg/windows-data-types">UINT</a>*</b>

Pointer to an array of stride values; one stride value for each buffer in the vertex-buffer array. Each stride is the size (in bytes) of the elements that are to be used from that vertex buffer.

### -param pOffsets [in, optional]

Type: <b>const <a href="/windows/desktop/WinProg/windows-data-types">UINT</a>*</b>

Pointer to an array of offset values; one offset value for each buffer in the vertex-buffer array. Each offset is the number of bytes between the first element of a vertex buffer and the first element that will be used.

## -remarks

For info about creating vertex buffers, see <a href="/windows/desktop/direct3d11/overviews-direct3d-11-resources-buffers-vertex-how-to">How to: Create a Vertex Buffer</a>.
        

Calling this method using a buffer that is currently bound for writing (that is, bound to the stream output pipeline stage) will effectively bind <b>NULL</b> instead because a buffer can't be bound as both an input and an output at the same time.
        

The debug layer will generate a warning whenever a resource is prevented from being bound simultaneously as an input and an output, but this will not prevent invalid data from being used by the runtime.

The method will hold a reference to the interfaces passed in.
          This differs from the device state behavior in Direct3D 10.
        

<b>Windows Phone 8:
        </b> This API is supported.

## -see-also

<a href="/windows/desktop/api/d3d11/nn-d3d11-id3d11devicecontext">ID3D11DeviceContext</a>