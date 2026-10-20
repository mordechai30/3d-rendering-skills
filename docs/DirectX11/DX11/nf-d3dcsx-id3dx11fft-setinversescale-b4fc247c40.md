Source: [https://learn.microsoft.com/en-us/windows/win32/api/d3dcsx/nf-d3dcsx-id3dx11fft-setinversescale](<https://learn.microsoft.com/en-us/windows/win32/api/d3dcsx/nf-d3dcsx-id3dx11fft-setinversescale>)

[Read in English](#)
[Edit](./nf-d3dcsx-id3dx11fft-setinversescale-b4fc247c40.md)


---

---

Note

# ID3DX11FFT::SetInverseScale method (d3dcsx.h)

Sets the scale used for inverse transforms.

## Syntax

```
HRESULT SetInverseScale(
  [in] FLOAT InverseScale
);
```

## Parameters

`[in] InverseScale`

Type: **[FLOAT](/en-us/windows/desktop/WinProg/windows-data-types)**

Scale used for inverse transforms. Setting *InverseScale* to 0 causes the default value of 1/N to be used,
where N is the product of the transformed dimension lengths.

## Return value

Type: **[HRESULT](/en-us/windows/win32/com/structure-of-com-error-codes)**

Returns one of the return codes described in the topic [Direct3D 11 Return Codes](./d3d11-graphics-reference-returnvalues-2d2638a6a7.md).

## Remarks

**SetInverseScale** sets the scale used by [ID3DX11FFT::InverseTransform](./nf-d3dcsx-id3dx11fft-inversetransform-58f1bd0a7c.md).

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