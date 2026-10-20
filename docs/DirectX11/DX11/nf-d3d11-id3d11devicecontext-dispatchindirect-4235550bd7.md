Source: [https://learn.microsoft.com/en-us/windows/win32/api/D3D11/nf-d3d11-id3d11devicecontext-dispatchindirect](<https://learn.microsoft.com/en-us/windows/win32/api/D3D11/nf-d3d11-id3d11devicecontext-dispatchindirect>)

# ID3D11DeviceContext::DispatchIndirect


## -description

Execute a command list over one or more thread groups.

## -parameters

### -param pBufferForArgs [in]

Type: <b><a href="/windows/desktop/api/d3d11/nn-d3d11-id3d11buffer">ID3D11Buffer</a>*</b>

A pointer to an <a href="/windows/desktop/api/d3d11/nn-d3d11-id3d11buffer">ID3D11Buffer</a>, which must be loaded with data that matches the argument list for <a href="/windows/desktop/api/d3d11/nf-d3d11-id3d11devicecontext-dispatch">ID3D11DeviceContext::Dispatch</a>.

### -param AlignedByteOffsetForArgs [in]

Type: <b><a href="/windows/desktop/WinProg/windows-data-types">UINT</a></b>

A byte-aligned offset between the start of the buffer and the arguments.

## -remarks

You call the <b>DispatchIndirect</b> method to execute commands in a <a href="/windows/desktop/direct3d11/direct3d-11-advanced-stages-compute-shader">compute shader</a>.

When an application creates a buffer that is associated with the <a href="/windows/desktop/api/d3d11/nn-d3d11-id3d11buffer">ID3D11Buffer</a> interface that  <i>pBufferForArgs</i> points to, the application must set the <a href="/windows/desktop/api/d3d11/ne-d3d11-d3d11_resource_misc_flag">D3D11_RESOURCE_MISC_DRAWINDIRECT_ARGS</a> flag in the <b>MiscFlags</b> member of the <a href="/windows/desktop/api/d3d11/ns-d3d11-d3d11_buffer_desc">D3D11_BUFFER_DESC</a> structure that describes the buffer. To create the buffer, the application calls the <a href="/windows/desktop/api/d3d11/nf-d3d11-id3d11device-createbuffer">ID3D11Device::CreateBuffer</a> method and in this call passes a pointer to <b>D3D11_BUFFER_DESC</b> in the <i>pDesc</i> parameter.

## -see-also

<a href="/windows/desktop/api/d3d11/nn-d3d11-id3d11devicecontext">ID3D11DeviceContext</a>