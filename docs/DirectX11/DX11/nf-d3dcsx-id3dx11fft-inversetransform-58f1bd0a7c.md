Source: [https://learn.microsoft.com/en-us/windows/win32/api/d3dcsx/nf-d3dcsx-id3dx11fft-inversetransform](<https://learn.microsoft.com/en-us/windows/win32/api/d3dcsx/nf-d3dcsx-id3dx11fft-inversetransform>)

[Read in English](#)
[Edit](./nf-d3dcsx-id3dx11fft-inversetransform-58f1bd0a7c.md)


---

---

Note

# ID3DX11FFT::InverseTransform method (d3dcsx.h)

Performs an inverse FFT.

## Syntax

```
HRESULT InverseTransform(
  [in]      const ID3D11UnorderedAccessView *pInputBuffer,
  [in, out] ID3D11UnorderedAccessView       **ppOutputBuffer
);
```

## Parameters

`[in] pInputBuffer`

Type: **const [ID3D11UnorderedAccessView](./nn-d3d11-id3d11unorderedaccessview-837aae35d2.md)\***

Pointer to [ID3D11UnorderedAccessView](./nn-d3d11-id3d11unorderedaccessview-837aae35d2.md) onto the input buffer.

`[in, out] ppOutputBuffer`

Type: **[ID3D11UnorderedAccessView](./nn-d3d11-id3d11unorderedaccessview-837aae35d2.md)\*\***

Pointer to a [ID3D11UnorderedAccessView](./nn-d3d11-id3d11unorderedaccessview-837aae35d2.md) pointer. If \**ppOutput* is **NULL**, then the computation will switch
between temp buffers; in addition, the last buffer written to is stored at \**ppOutput*.
Otherwise, \**ppOutput* is used as the output buffer (which might incur an extra copy).

## Return value

Type: **[HRESULT](/en-us/windows/win32/com/structure-of-com-error-codes)**

Returns one of the return codes described in the topic [Direct3D 11 Return Codes](./d3d11-graphics-reference-returnvalues-2d2638a6a7.md).

## Requirements

| Requirement | Value |
| --- | --- |
| **Target Platform** | Windows |
| **Header** | d3dcsx.h |
| **Library** | D3dcsx.lib |

## See also

[ID3DX11FFT](./nn-d3dcsx-id3dx11fft-2df111057b.md)

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