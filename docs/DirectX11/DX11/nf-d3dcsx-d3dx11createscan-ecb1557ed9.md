Source: [https://learn.microsoft.com/en-us/windows/win32/api/d3dcsx/nf-d3dcsx-d3dx11createscan](<https://learn.microsoft.com/en-us/windows/win32/api/d3dcsx/nf-d3dcsx-d3dx11createscan>)

[Read in English](#)
[Edit](./nf-d3dcsx-d3dx11createscan-ecb1557ed9.md)


---

---

Note

# D3DX11CreateScan function (d3dcsx.h)

Creates a scan context.

## Syntax

```
HRESULT D3DX11CreateScan(
  [in]  ID3D11DeviceContext *pDeviceContext,
        UINT                MaxElementScanSize,
        UINT                MaxScanCount,
  [out] ID3DX11Scan         **ppScan
);
```

## Parameters

`[in] pDeviceContext`

Type: **[ID3D11DeviceContext](./nn-d3d11-id3d11devicecontext-abe911f651.md)\***

The [ID3D11DeviceContext](./nn-d3d11-id3d11devicecontext-abe911f651.md) the scan is associated with.

`MaxElementScanSize`

Type: **[UINT](/en-us/windows/desktop/WinProg/windows-data-types)**

Maximum single scan size, in elements (FLOAT, UINT, or INT).

`MaxScanCount`

Type: **[UINT](/en-us/windows/desktop/WinProg/windows-data-types)**

Maximum number of scans in multiscan.

`[out] ppScan`

Type: **[ID3DX11Scan](./nn-d3dcsx-id3dx11scan-ec7e6b33a7.md)\*\***

Pointer to a [ID3DX11Scan Interface](./nn-d3dcsx-id3dx11scan-ec7e6b33a7.md) pointer that will be set to the created interface object.

## Return value

Type: **[HRESULT](/en-us/windows/win32/com/structure-of-com-error-codes)**

The return value is one of the values listed in [Direct3D 11 Return Codes](./d3d11-graphics-reference-returnvalues-2d2638a6a7.md).

## Requirements

| Requirement | Value |
| --- | --- |
| **Target Platform** | Windows |
| **Header** | d3dcsx.h |
| **Library** | D3dcsx.lib |

## See also

[D3DCSX 11 Functions](./d3d11-graphics-reference-d3dcsx11-functions-1fa174523c.md)

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