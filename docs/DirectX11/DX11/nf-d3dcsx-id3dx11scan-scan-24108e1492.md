Source: [https://learn.microsoft.com/en-us/windows/win32/api/d3dcsx/nf-d3dcsx-id3dx11scan-scan](<https://learn.microsoft.com/en-us/windows/win32/api/d3dcsx/nf-d3dcsx-id3dx11scan-scan>)

[Read in English](#)
[Edit](./nf-d3dcsx-id3dx11scan-scan-24108e1492.md)


---

---

Note

# ID3DX11Scan::Scan method (d3dcsx.h)

Performs an unsegmented scan of a sequence.

## Syntax

```
HRESULT Scan(
  [in] D3DX11_SCAN_DATA_TYPE     ElementType,
  [in] D3DX11_SCAN_OPCODE        OpCode,
  [in] UINT                      ElementScanSize,
  [in] ID3D11UnorderedAccessView *pSrc,
  [in] ID3D11UnorderedAccessView *pDst
);
```

## Parameters

`[in] ElementType`

Type: **[D3DX11\_SCAN\_DATA\_TYPE](./ne-d3dcsx-d3dx11_scan_data_type-2f71efdf44.md)**

The type of element in the sequence. See [D3DX11\_SCAN\_DATA\_TYPE](./ne-d3dcsx-d3dx11_scan_data_type-2f71efdf44.md) for more information.

`[in] OpCode`

Type: **[D3DX11\_SCAN\_OPCODE](./ne-d3dcsx-d3dx11_scan_opcode-25780db583.md)**

The binary operation to perform. See [D3DX11\_SCAN\_OPCODE](./ne-d3dcsx-d3dx11_scan_opcode-25780db583.md) for more information.

`[in] ElementScanSize`

Type: **[UINT](/en-us/windows/desktop/WinProg/windows-data-types)**

Size of scan in elements.

`[in] pSrc`

Type: **[ID3D11UnorderedAccessView](./nn-d3d11-id3d11unorderedaccessview-837aae35d2.md)\***

Input sequence on the device. Set *pSrc* and *pDst* to the same value for in-place scans.

`[in] pDst`

Type: **[ID3D11UnorderedAccessView](./nn-d3d11-id3d11unorderedaccessview-837aae35d2.md)\***

Output sequence on the device.

## Return value

Type: **[HRESULT](/en-us/windows/win32/com/structure-of-com-error-codes)**

Returns one of the return codes described in the topic [Direct3D 11 Return Codes](./d3d11-graphics-reference-returnvalues-2d2638a6a7.md).

## Remarks

You must point the parameters *pSrc* and *pDst* to typed buffers (and not to raw or structured buffers). For information about buffer types, see [Types of Resources](./overviews-direct3d-11-resources-types-0fad49d3cf.md). The format of these typed buffers must be [DXGI\_FORMAT\_R32\_FLOAT](/en-us/windows/desktop/api/dxgiformat/ne-dxgiformat-dxgi_format), **DXGI\_FORMAT\_R32\_UINT**, or **DXGI\_FORMAT\_R32\_INT**. In addition, the format of these typed buffers must match the scan data type that you specify in the *ElementType* parameter. For example, if the scan data type is [D3DX11\_SCAN\_DATA\_TYPE\_UINT](./ne-d3dcsx-d3dx11_scan_data_type-2f71efdf44.md), the buffer formats must be **DXGI\_FORMAT\_R32\_UINT**.

## Requirements

| Requirement | Value |
| --- | --- |
| **Target Platform** | Windows |
| **Header** | d3dcsx.h |
| **Library** | D3dcsx.lib |

## See also

[ID3DX11Scan](./nn-d3dcsx-id3dx11scan-ec7e6b33a7.md)

---

## Feedback

Was this page helpful?

No

Need help with this topic?

Want to try using Ask Learn to clarify or guide you through this topic?

---

## Additional resources

---

* Last updated on 
  2024-02-22