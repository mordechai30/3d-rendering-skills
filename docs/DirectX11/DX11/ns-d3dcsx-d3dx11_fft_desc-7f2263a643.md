Source: [https://learn.microsoft.com/en-us/windows/win32/api/d3dcsx/ns-d3dcsx-d3dx11_fft_desc](<https://learn.microsoft.com/en-us/windows/win32/api/d3dcsx/ns-d3dcsx-d3dx11_fft_desc>)

[Read in English](#)
[Edit](./ns-d3dcsx-d3dx11_fft_desc-7f2263a643.md)


---

---

Note

# D3DX11\_FFT\_DESC structure (d3dcsx.h)

Describes an FFT.

## Syntax

```
typedef struct D3DX11_FFT_DESC {
  UINT                 NumDimensions;
  UINT                 ElementLengths[D3DX11_FFT_MAX_DIMENSIONS];
  UINT                 DimensionMask;
  D3DX11_FFT_DATA_TYPE Type;
} D3DX11_FFT_DESC;
```

## Members

`NumDimensions`

Type: **[UINT](/en-us/windows/desktop/WinProg/windows-data-types)**

Number of dimension in the FFT.

`ElementLengths[D3DX11_FFT_MAX_DIMENSIONS]`

Type: **[UINT](/en-us/windows/desktop/WinProg/windows-data-types)[D3DX11\_FFT\_MAX\_DIMENSIONS]**

Length of each dimension in the FFT.

`DimensionMask`

Type: **[UINT](/en-us/windows/desktop/WinProg/windows-data-types)**

Combination of [D3DX11\_FFT\_DIM\_MASK](./ne-d3dcsx-d3dx11_fft_dim_mask-337bdaac9a.md) flags indicating the dimensions to transform.

`Type`

Type: **[D3DX11\_FFT\_DATA\_TYPE](./ne-d3dcsx-d3dx11_fft_data_type-b019d32ef6.md)**

[D3DX11\_FFT\_DATA\_TYPE](./ne-d3dcsx-d3dx11_fft_data_type-b019d32ef6.md) flag indicating the type of data being transformed.

## Requirements

| Requirement | Value |
| --- | --- |
| **Header** | d3dcsx.h |

## See also

[D3DCSX 11 Structures](./d3d11-graphics-reference-d3dcsx11-structures-05b8dadcb7.md)

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