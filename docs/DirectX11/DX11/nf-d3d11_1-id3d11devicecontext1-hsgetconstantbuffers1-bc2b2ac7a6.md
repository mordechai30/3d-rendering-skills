Source: [https://learn.microsoft.com/en-us/windows/win32/api/D3D11_1/nf-d3d11_1-id3d11devicecontext1-hsgetconstantbuffers1](<https://learn.microsoft.com/en-us/windows/win32/api/D3D11_1/nf-d3d11_1-id3d11devicecontext1-hsgetconstantbuffers1>)

# ID3D11DeviceContext1::HSGetConstantBuffers1


## -description

Gets the constant buffers that the <a href="/windows/desktop/direct3d11/direct3d-11-advanced-stages-tessellation">hull-shader stage</a> uses.

## -parameters

### -param StartSlot [in]

Index into the device's zero-based array to begin retrieving constant buffers from (ranges from 0 to D3D11_COMMONSHADER_CONSTANT_BUFFER_API_SLOT_COUNT - 1).

### -param NumBuffers [in]

Number of buffers to retrieve (ranges from 0 to D3D11_COMMONSHADER_CONSTANT_BUFFER_API_SLOT_COUNT - <i>StartSlot</i>).

### -param ppConstantBuffers [out, optional]

Array of constant buffer interface pointers to be returned by the method.

### -param pFirstConstant [out, optional]

A pointer to an array that receives the offsets into the buffers that  <i>ppConstantBuffers</i> specifies. Each offset specifies where, from the shader's point of view, each constant buffer starts.  Each offset is measured in shader constants, which are 16 bytes (4*32-bit components).  Therefore, an offset of 2 indicates that the start of the associated constant buffer is 32 bytes into the constant buffer. The runtime sets <i>pFirstConstant</i> to <b>NULL</b> if the buffers do not have offsets.

### -param pNumConstants [out, optional]

A pointer to an array that receives the numbers of constants in the buffers that  <i>ppConstantBuffers</i> specifies. Each number specifies the number of constants that are contained in the constant buffer that the shader uses. Each number of constants starts from its respective offset that is specified in the <i>pFirstConstant</i> array. The runtime sets <i>pNumConstants</i> to <b>NULL</b> if it doesn't specify the numbers of constants in each buffer.

## -remarks

If no buffer is bound at a slot, <i>pFirstConstant</i> and <i>pNumConstants</i> are <b>NULL</b> for that slot.

## -see-also

<a href="/windows/desktop/api/d3d11_1/nn-d3d11_1-id3d11devicecontext1">ID3D11DeviceContext1</a>