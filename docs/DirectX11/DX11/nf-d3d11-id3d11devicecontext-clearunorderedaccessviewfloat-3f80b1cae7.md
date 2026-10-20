Source: [https://learn.microsoft.com/en-us/windows/win32/api/D3D11/nf-d3d11-id3d11devicecontext-clearunorderedaccessviewfloat](<https://learn.microsoft.com/en-us/windows/win32/api/D3D11/nf-d3d11-id3d11devicecontext-clearunorderedaccessviewfloat>)

# ID3D11DeviceContext::ClearUnorderedAccessViewFloat


## -description

Clears an <a href="/windows/desktop/direct3d11/direct3d-11-advanced-stages-cs-resources">unordered access</a> resource with a float value.

## -parameters

### -param pUnorderedAccessView [in]

Type: <b><a href="/windows/desktop/api/d3d11/nn-d3d11-id3d11unorderedaccessview">ID3D11UnorderedAccessView</a>*</b>

The <a href="/windows/desktop/api/d3d11/nn-d3d11-id3d11unorderedaccessview">ID3D11UnorderedAccessView</a> to clear.

### -param Values [in]

Type: <b>const FLOAT[4]</b>

Values to copy to corresponding channels, see remarks.

## -remarks

This API works on FLOAT, UNORM, and SNORM unordered access views (UAVs), with format conversion from FLOAT to *NORM where appropriate. On other UAVs, the operation is invalid and the call will not reach the driver.

## -see-also

<a href="/windows/desktop/api/d3d11/nn-d3d11-id3d11devicecontext">ID3D11DeviceContext</a>