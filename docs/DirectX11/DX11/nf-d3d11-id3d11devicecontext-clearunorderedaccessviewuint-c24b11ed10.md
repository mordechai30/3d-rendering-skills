Source: [https://learn.microsoft.com/en-us/windows/win32/api/D3D11/nf-d3d11-id3d11devicecontext-clearunorderedaccessviewuint](<https://learn.microsoft.com/en-us/windows/win32/api/D3D11/nf-d3d11-id3d11devicecontext-clearunorderedaccessviewuint>)

# ID3D11DeviceContext::ClearUnorderedAccessViewUint


## -description

Clears an <a href="/windows/desktop/direct3d11/direct3d-11-advanced-stages-cs-resources">unordered access</a> resource with bit-precise values.

## -parameters

### -param pUnorderedAccessView [in]

Type: <b><a href="/windows/desktop/api/d3d11/nn-d3d11-id3d11unorderedaccessview">ID3D11UnorderedAccessView</a>*</b>

The <a href="/windows/desktop/api/d3d11/nn-d3d11-id3d11unorderedaccessview">ID3D11UnorderedAccessView</a> to clear.

### -param Values [in]

Type: <b>const <a href="/windows/desktop/WinProg/windows-data-types">UINT</a>[4]</b>

Values to copy to corresponding channels, see remarks.

## -remarks

This API copies the lower n<sub>i</sub> bits from each array element i to the corresponding channel, where n<sub>i</sub> is the number of bits in 
      the ith channel of the resource format (for example, R8G8B8_FLOAT has 8 bits for the first 3 channels). This works on any UAV with no format conversion. 
      For a raw or structured buffer view, only the first array element value is used.

## -see-also

<a href="/windows/desktop/api/d3d11/nn-d3d11-id3d11devicecontext">ID3D11DeviceContext</a>