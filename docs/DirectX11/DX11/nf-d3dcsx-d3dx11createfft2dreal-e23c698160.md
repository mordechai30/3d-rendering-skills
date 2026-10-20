Source: [https://learn.microsoft.com/en-us/windows/win32/api/d3dcsx/nf-d3dcsx-d3dx11createfft2dreal](<https://learn.microsoft.com/en-us/windows/win32/api/d3dcsx/nf-d3dcsx-d3dx11createfft2dreal>)

[Read in English](#)
[Edit](./nf-d3dcsx-d3dx11createfft2dreal-e23c698160.md)


---

---

Note

# D3DX11CreateFFT2DReal function (d3dcsx.h)

Creates an [ID3DX11FFT](./nn-d3dcsx-id3dx11fft-2df111057b.md) COM interface object.

## Syntax

```
HRESULT D3DX11CreateFFT2DReal(
        ID3D11DeviceContext    *pDeviceContext,
        UINT                   X,
        UINT                   Y,
        UINT                   Flags,
  [out] D3DX11_FFT_BUFFER_INFO *pBufferInfo,
  [out] ID3DX11FFT             **ppFFT
);
```

## Parameters

`pDeviceContext`

Type: **[ID3D11DeviceContext](./nn-d3d11-id3d11devicecontext-abe911f651.md)\***

A pointer to the [ID3D11DeviceContext](./nn-d3d11-id3d11devicecontext-abe911f651.md) interface to use for the FFT.

`X`

Type: **[UINT](/en-us/windows/desktop/WinProg/windows-data-types)**

Length of the first dimension of the FFT.

`Y`

Type: **[UINT](/en-us/windows/desktop/WinProg/windows-data-types)**

Length of the second dimension of the FFT.

`Flags`

Type: **[UINT](/en-us/windows/desktop/WinProg/windows-data-types)**

Flags that affect the behavior of the FFT, can be 0 or a combination of flags from [D3DX11\_FFT\_CREATE\_FLAG](./ne-d3dcsx-d3dx11_fft_create_flag-280bd6ac1a.md).

`[out] pBufferInfo`

Type: **[D3DX11\_FFT\_BUFFER\_INFO](./ns-d3dcsx-d3dx11_fft_buffer_info-1c175ba278.md)\***

A pointer to a [D3DX11\_FFT\_BUFFER\_INFO](./ns-d3dcsx-d3dx11_fft_buffer_info-1c175ba278.md) structure that receives the buffer requirements to execute the FFT algorithms. Use this info to allocate raw buffers of the specified (or larger) sizes and then call the [ID3DX11FFT::AttachBuffersAndPrecompute](./nf-d3dcsx-id3dx11fft-attachbuffersandprecompute-371540973b.md) method to register the buffers with the FFT object.

`[out] ppFFT`

Type: **[ID3DX11FFT](./nn-d3dcsx-id3dx11fft-2df111057b.md)\*\***

A pointer to a variable that receives a pointer to the [ID3DX11FFT](./nn-d3dcsx-id3dx11fft-2df111057b.md) interface for the created FFT object.

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