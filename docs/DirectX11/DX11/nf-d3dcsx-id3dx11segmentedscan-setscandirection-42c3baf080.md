Source: [https://learn.microsoft.com/en-us/windows/win32/api/d3dcsx/nf-d3dcsx-id3dx11segmentedscan-setscandirection](<https://learn.microsoft.com/en-us/windows/win32/api/d3dcsx/nf-d3dcsx-id3dx11segmentedscan-setscandirection>)

[Read in English](#)
[Edit](./nf-d3dcsx-id3dx11segmentedscan-setscandirection-42c3baf080.md)


---

---

Note

# ID3DX11SegmentedScan::SetScanDirection method (d3dcsx.h)

Sets which direction to perform scans in.

## Syntax

```
HRESULT SetScanDirection(
  [in] D3DX11_SCAN_DIRECTION Direction
);
```

## Parameters

`[in] Direction`

Type: **[D3DX11\_SCAN\_DIRECTION](./ne-d3dcsx-d3dx11_scan_direction-fe30506e99.md)**

Direction to perform scans in. See [D3DX11\_SCAN\_DIRECTION](./ne-d3dcsx-d3dx11_scan_direction-fe30506e99.md).

## Return value

Type: **[HRESULT](/en-us/windows/win32/com/structure-of-com-error-codes)**

Returns one of the return codes described in the topic [Direct3D 11 Return Codes](./d3d11-graphics-reference-returnvalues-2d2638a6a7.md).

## Remarks

**SetScanDirection** sets the direction [ID3DX11SegmentedScan::SegScan](./nf-d3dcsx-id3dx11segmentedscan-segscan-de353aeb24.md) will performed scans in.

## Requirements

| Requirement | Value |
| --- | --- |
| **Target Platform** | Windows |
| **Header** | d3dcsx.h |
| **Library** | D3dcsx.lib |

## See also

[ID3DX11SegmentedScan](./nn-d3dcsx-id3dx11segmentedscan-3ee2619eaf.md)

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