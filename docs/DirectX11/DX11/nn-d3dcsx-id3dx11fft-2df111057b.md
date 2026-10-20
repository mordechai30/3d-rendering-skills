Source: [https://learn.microsoft.com/en-us/windows/win32/api/d3dcsx/nn-d3dcsx-id3dx11fft](<https://learn.microsoft.com/en-us/windows/win32/api/d3dcsx/nn-d3dcsx-id3dx11fft>)

[Read in English](#)
[Edit](./nn-d3dcsx-id3dx11fft-2df111057b.md)


---

---

Note

# ID3DX11FFT interface (d3dcsx.h)

Encapsulates forward and inverse FFTs.

## Inheritance

The **ID3DX11FFT** interface inherits from the [IUnknown](/en-us/windows/desktop/api/unknwn/nn-unknwn-iunknown) interface. **ID3DX11FFT** also has these types of members:

## Methods

The **ID3DX11FFT** interface has these methods.

|  |
| --- |
| [ID3DX11FFT::AttachBuffersAndPrecompute](./nf-d3dcsx-id3dx11fft-attachbuffersandprecompute-371540973b.md)   Attaches buffers to an FFT context and performs any required precomputations. |
| [ID3DX11FFT::ForwardTransform](./nf-d3dcsx-id3dx11fft-forwardtransform-6f4284e42a.md)   Performs a forward FFT. |
| [ID3DX11FFT::GetForwardScale](./nf-d3dcsx-id3dx11fft-getforwardscale-73c7c71f2c.md)   Gets the scale for forward transforms. |
| [ID3DX11FFT::GetInverseScale](./nf-d3dcsx-id3dx11fft-getinversescale-ccdf2a8eab.md)   Get the scale for inverse transforms. |
| [ID3DX11FFT::InverseTransform](./nf-d3dcsx-id3dx11fft-inversetransform-58f1bd0a7c.md)   Performs an inverse FFT. |
| [ID3DX11FFT::SetForwardScale](./nf-d3dcsx-id3dx11fft-setforwardscale-4b72bc4d36.md)   Sets the scale used for forward transforms. |
| [ID3DX11FFT::SetInverseScale](./nf-d3dcsx-id3dx11fft-setinversescale-b4fc247c40.md)   Sets the scale used for inverse transforms. |

## Requirements

| Requirement | Value |
| --- | --- |
| **Target Platform** | Windows |
| **Header** | d3dcsx.h |

## See also

[D3DCSX 11 Interfaces](./d3d11-graphics-reference-d3dcsx11-interfaces-078f57ce37.md)

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
  2021-07-22