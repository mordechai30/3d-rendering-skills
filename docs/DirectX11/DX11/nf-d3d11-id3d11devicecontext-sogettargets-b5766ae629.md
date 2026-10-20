Source: [https://learn.microsoft.com/en-us/windows/win32/api/D3D11/nf-d3d11-id3d11devicecontext-sogettargets](<https://learn.microsoft.com/en-us/windows/win32/api/D3D11/nf-d3d11-id3d11devicecontext-sogettargets>)

# ID3D11DeviceContext::SOGetTargets


## -description

Get the target output buffers for the stream-output stage of the pipeline.

## -parameters

### -param NumBuffers [in]

Type: <b><a href="/windows/desktop/WinProg/windows-data-types">UINT</a></b>

Number of buffers to get.

### -param ppSOTargets [out, optional]

Type: <b><a href="/windows/desktop/api/d3d11/nn-d3d11-id3d11buffer">ID3D11Buffer</a>**</b>

An array of output buffers (see <a href="/windows/desktop/api/d3d11/nn-d3d11-id3d11buffer">ID3D11Buffer</a>) to be retrieved from the device.

## -remarks

A maximum of four output buffers can be retrieved.

The offsets to the output buffers pointed to in the returned <i>ppSOTargets</i> array may be assumed to be -1 (append), as defined for use in <a href="/windows/desktop/api/d3d11/nf-d3d11-id3d11devicecontext-sosettargets">ID3D11DeviceContext::SOSetTargets</a>.
        

Any returned interfaces will have their reference count incremented by one. Applications should call IUnknown::Release on the returned interfaces when they are no longer needed to avoid memory leaks.

<b>Windows Phone 8:
        </b> This API is supported.

## -see-also

<a href="/windows/desktop/api/d3d11/nn-d3d11-id3d11devicecontext">ID3D11DeviceContext</a>