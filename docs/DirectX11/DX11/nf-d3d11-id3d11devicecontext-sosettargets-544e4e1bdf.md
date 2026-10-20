Source: [https://learn.microsoft.com/en-us/windows/win32/api/D3D11/nf-d3d11-id3d11devicecontext-sosettargets](<https://learn.microsoft.com/en-us/windows/win32/api/D3D11/nf-d3d11-id3d11devicecontext-sosettargets>)

# ID3D11DeviceContext::SOSetTargets


## -description

Set the target output buffers for the stream-output stage of the pipeline.

## -parameters

### -param NumBuffers [in]

Type: <b><a href="/windows/win32/winprog/windows-data-types">UINT</a></b>

The number of buffer to bind to the device. A maximum of four output buffers can be set. If less than four are defined by the call, the remaining buffer slots are set to <b>NULL</b>. See Remarks.

### -param ppSOTargets [in, optional]

Type: <b><a href="/windows/win32/api/d3d11/nn-d3d11-id3d11buffer">ID3D11Buffer</a>*</b>

The array of output buffers (see <a href="/windows/win32/api/d3d11/nn-d3d11-id3d11buffer">ID3D11Buffer</a>) to bind to the device. The buffers must have been created with the <a href="/windows/win32/api/d3d11/ne-d3d11-d3d11_bind_flag">D3D11_BIND_STREAM_OUTPUT</a> flag.

### -param pOffsets [in, optional]

Type: <b>const <a href="/windows/win32/winprog/windows-data-types">UINT</a>*</b>

Array of offsets to the output buffers from <i>ppSOTargets</i>, one offset for each buffer. The offset values must be in bytes.

## -remarks

An offset of -1 will cause the stream output buffer to be appended, continuing after the last location written to the buffer in a previous stream output pass.

Calling this method using a buffer that is currently bound for writing will effectively bind <b>NULL</b> instead because a buffer cannot be bound as both an input and an output at the same time.
        

The debug layer will generate a warning whenever a resource is prevented from being bound simultaneously as an input and an output, but this will not prevent invalid data from being used by the runtime.

The method will hold a reference to the interfaces passed in.
          This differs from the device state behavior in Direct3D 10.

Note that unlike some other resource methods in Direct3D, all currently bound targets will be unbound by calling `SOSetTargets(0, nullptr, nullptr);`.

<b>Windows Phone 8:
        </b> This API is supported.

## -see-also

<a href="/windows/win32/api/d3d11/nn-d3d11-id3d11devicecontext">ID3D11DeviceContext</a>