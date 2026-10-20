Source: [https://learn.microsoft.com/en-us/windows/win32/api/d3dcsx/ne-d3dcsx-d3dx11_fft_create_flag](<https://learn.microsoft.com/en-us/windows/win32/api/d3dcsx/ne-d3dcsx-d3dx11_fft_create_flag>)

[Read in English](#)
[Edit](./ne-d3dcsx-d3dx11_fft_create_flag-280bd6ac1a.md)


---

---

Note

# D3DX11\_FFT\_CREATE\_FLAG enumeration (d3dcsx.h)

FFT creation flags.

## Syntax

```
typedef enum D3DX11_FFT_CREATE_FLAG {
  D3DX11_FFT_CREATE_FLAG_NO_PRECOMPUTE_BUFFERS = 0x01L
} ;
```

## Constants

|  |
| --- |
| `D3DX11_FFT_CREATE_FLAG_NO_PRECOMPUTE_BUFFERS` Value: *0x01L* Do not AddRef or Release temp and precompute buffers, caller is responsible for holding   references to these buffers. |

## Requirements

| Requirement | Value |
| --- | --- |
| **Header** | d3dcsx.h |

## See also

[D3DCSX 11 Enumerations](./d3d11-graphics-reference-d3dcsx11-enums-800f8e2ec0.md)

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