Source: [https://learn.microsoft.com/en-us/windows/win32/api/d3dcsx/nf-d3dcsx-id3dx11fft-forwardtransform](<https://learn.microsoft.com/en-us/windows/win32/api/d3dcsx/nf-d3dcsx-id3dx11fft-forwardtransform>)

[Read in English](#)
[Edit](./nf-d3dcsx-id3dx11fft-forwardtransform-6f4284e42a.md)


---

---

Note

# ID3DX11FFT::ForwardTransform method (d3dcsx.h)

Performs a forward FFT.

## Syntax

```
HRESULT ForwardTransform(
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

Pointer to a [ID3D11UnorderedAccessView](./nn-d3d11-id3d11unorderedaccessview-837aae35d2.md) pointer. If \**ppOutputBuffer* is **NULL**, the computation will switch
between temp buffers; in addition, the last buffer written to is stored at \**ppOutputBuffer*.
Otherwise, \**ppOutputBuffer* is used as the output buffer (which might incur an extra copy).

## Return value

Type: **[HRESULT](/en-us/windows/win32/com/structure-of-com-error-codes)**

Returns one of the return codes described in the topic [Direct3D 11 Return Codes](./d3d11-graphics-reference-returnvalues-2d2638a6a7.md).

## Remarks

**ForwardTransform** can be called after buffers have been attached to the context using [ID3DX11FFT::AttachBuffersAndPrecompute](./nf-d3dcsx-id3dx11fft-attachbuffersandprecompute-371540973b.md). The combination of *pInputBuffer* and \**ppOutputBuffer* can be one of the temp buffers.

The format of complex data is interleaved components (for example, (Real0, Imag0),
(Real1, Imag1) ... , and so on). Data is stored in row major order.

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