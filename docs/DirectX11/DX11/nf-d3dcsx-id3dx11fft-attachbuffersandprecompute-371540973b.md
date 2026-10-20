Source: [https://learn.microsoft.com/en-us/windows/win32/api/d3dcsx/nf-d3dcsx-id3dx11fft-attachbuffersandprecompute](<https://learn.microsoft.com/en-us/windows/win32/api/d3dcsx/nf-d3dcsx-id3dx11fft-attachbuffersandprecompute>)

[Read in English](#)
[Edit](./nf-d3dcsx-id3dx11fft-attachbuffersandprecompute-371540973b.md)


---

---

Note

# ID3DX11FFT::AttachBuffersAndPrecompute method (d3dcsx.h)

Attaches buffers to an FFT context and performs any required precomputations.

## Syntax

```
HRESULT AttachBuffersAndPrecompute(
  [in] UINT                      NumTempBuffers,
  [in] ID3D11UnorderedAccessView * const *ppTempBuffers,
  [in] UINT                      NumPrecomputeBuffers,
  [in] ID3D11UnorderedAccessView * const *ppPrecomputeBufferSizes
);
```

## Parameters

`[in] NumTempBuffers`

Type: **[UINT](/en-us/windows/desktop/WinProg/windows-data-types)**

Number of buffers in *ppTempBuffers*.

`[in] ppTempBuffers`

Type: **[ID3D11UnorderedAccessView](./nn-d3d11-id3d11unorderedaccessview-837aae35d2.md)\***

A pointer to an array of [ID3D11UnorderedAccessView](./nn-d3d11-id3d11unorderedaccessview-837aae35d2.md) pointers for the temporary buffers to attach. The FFT object might use these temporary buffers for its algorithm.

`[in] NumPrecomputeBuffers`

Type: **[UINT](/en-us/windows/desktop/WinProg/windows-data-types)**

Number of buffers in *ppPrecomputeBuffers*.

`[in] ppPrecomputeBufferSizes`

Type: **[ID3D11UnorderedAccessView](./nn-d3d11-id3d11unorderedaccessview-837aae35d2.md)\***

A pointer to an array of [ID3D11UnorderedAccessView](./nn-d3d11-id3d11unorderedaccessview-837aae35d2.md) pointers for the precompute buffers to attach. The FFT object might store precomputed data in these buffers.

## Return value

Type: **[HRESULT](/en-us/windows/win32/com/structure-of-com-error-codes)**

Returns one of the return codes described in the topic [Direct3D 11 Return Codes](./d3d11-graphics-reference-returnvalues-2d2638a6a7.md).

## Remarks

The [D3DX11\_FFT\_BUFFER\_INFO](./ns-d3dcsx-d3dx11_fft_buffer_info-1c175ba278.md) structure is initialized by a call to one of the create-FFT functions
(for example, [D3DX11CreateFFT](./nf-d3dcsx-d3dx11createfft-22cc7fd82b.md)). For more create-FFT functions, see [D3DCSX 11 Functions](./d3d11-graphics-reference-d3dcsx11-functions-1fa174523c.md).

Use the info in [D3DX11\_FFT\_BUFFER\_INFO](./ns-d3dcsx-d3dx11_fft_buffer_info-1c175ba278.md) to allocate raw buffers of the specified (or larger) sizes and then call the **AttachBuffersAndPrecompute** to register the buffers with the FFT object.

Although you can share temporary buffers between multiple
device contexts, we recommend not to concurrently execute multiple FFT objects that share temporary buffers.

Some FFT algorithms benefit from precomputing sin and cos. The FFT object might store precomputed data in the user-supplied precompute buffers.

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