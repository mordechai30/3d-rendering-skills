Source: [https://learn.microsoft.com/en-us/windows/win32/api/d3dcsx/ns-d3dcsx-d3dx11_fft_buffer_info](<https://learn.microsoft.com/en-us/windows/win32/api/d3dcsx/ns-d3dcsx-d3dx11_fft_buffer_info>)

[Read in English](#)
[Edit](./ns-d3dcsx-d3dx11_fft_buffer_info-1c175ba278.md)


---

---

Note

# D3DX11\_FFT\_BUFFER\_INFO structure (d3dcsx.h)

Describes buffer requirements for an FFT.

## Syntax

```
typedef struct D3DX11_FFT_BUFFER_INFO {
  UINT NumTempBufferSizes;
  UINT TempBufferFloatSizes[D3DX11_FFT_MAX_TEMP_BUFFERS];
  UINT NumPrecomputeBufferSizes;
  UINT PrecomputeBufferFloatSizes[D3DX11_FFT_MAX_PRECOMPUTE_BUFFERS];
} D3DX11_FFT_BUFFER_INFO;
```

## Members

`NumTempBufferSizes`

Type: **[UINT](/en-us/windows/desktop/WinProg/windows-data-types)**

Number of temporary buffers needed.
Allowed range is 0 to **D3DX11\_FFT\_MAX\_TEMP\_BUFFERS**.

`TempBufferFloatSizes[D3DX11_FFT_MAX_TEMP_BUFFERS]`

Type: **[UINT](/en-us/windows/desktop/WinProg/windows-data-types)[D3DX11\_FFT\_MAX\_TEMP\_BUFFERS]**

Minimum sizes (in FLOATs) of temporary buffers.

`NumPrecomputeBufferSizes`

Type: **[UINT](/en-us/windows/desktop/WinProg/windows-data-types)**

Number of precompute buffers required.  
Allowed range is 0 to **D3DX11\_FFT\_MAX\_PRECOMPUTE\_BUFFERS**.

`PrecomputeBufferFloatSizes[D3DX11_FFT_MAX_PRECOMPUTE_BUFFERS]`

Type: **[UINT](/en-us/windows/desktop/WinProg/windows-data-types)[D3DX11\_FFT\_MAX\_PRECOMPUTE\_BUFFERS]**

Minimum sizes (in FLOATs) for precompute buffers.

## Remarks

The **D3DX11\_FFT\_BUFFER\_INFO** structure is initialized by a call to one of the create-FFT functions
(for example, [D3DX11CreateFFT](./nf-d3dcsx-d3dx11createfft-22cc7fd82b.md)).
For more create-FFT functions, see [D3DCSX 11 Functions](./d3d11-graphics-reference-d3dcsx11-functions-1fa174523c.md).

Use the info in **D3DX11\_FFT\_BUFFER\_INFO** to allocate raw buffers of the specified (or larger) sizes and then call the [ID3DX11FFT::AttachBuffersAndPrecompute](./nf-d3dcsx-id3dx11fft-attachbuffersandprecompute-371540973b.md) method to register the buffers with the FFT object.

Some FFT algorithms benefit from precomputing sin and cos. The FFT object might store precomputed data in the user-supplied buffers.

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