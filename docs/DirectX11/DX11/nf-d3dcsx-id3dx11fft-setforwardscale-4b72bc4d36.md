Source: [https://learn.microsoft.com/en-us/windows/win32/api/d3dcsx/nf-d3dcsx-id3dx11fft-setforwardscale](<https://learn.microsoft.com/en-us/windows/win32/api/d3dcsx/nf-d3dcsx-id3dx11fft-setforwardscale>)

[Read in English](#)
[Edit](./nf-d3dcsx-id3dx11fft-setforwardscale-4b72bc4d36.md)


---

---

Note

# ID3DX11FFT::SetForwardScale method (d3dcsx.h)

Sets the scale used for forward transforms.

## Syntax

```
HRESULT SetForwardScale(
  [in] FLOAT ForwardScale
);
```

## Parameters

`[in] ForwardScale`

Type: **[FLOAT](/en-us/windows/desktop/WinProg/windows-data-types)**

The scale to use for forward transforms. Setting *ForwardScale* to 0 causes the default values of 1 to be used.

## Return value

Type: **[HRESULT](/en-us/windows/win32/com/structure-of-com-error-codes)**

Returns one of the return codes described in the topic [Direct3D 11 Return Codes](./d3d11-graphics-reference-returnvalues-2d2638a6a7.md).

## Remarks

**SetForwardScale** sets the scale used by [ID3DX11FFT::ForwardTransform](./nf-d3dcsx-id3dx11fft-forwardtransform-6f4284e42a.md).

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