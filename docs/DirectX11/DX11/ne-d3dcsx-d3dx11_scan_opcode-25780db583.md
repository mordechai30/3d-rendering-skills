Source: [https://learn.microsoft.com/en-us/windows/win32/api/d3dcsx/ne-d3dcsx-d3dx11_scan_opcode](<https://learn.microsoft.com/en-us/windows/win32/api/d3dcsx/ne-d3dcsx-d3dx11_scan_opcode>)

[Read in English](#)
[Edit](./ne-d3dcsx-d3dx11_scan_opcode-25780db583.md)


---

---

Note

# D3DX11\_SCAN\_OPCODE enumeration (d3dcsx.h)

Scan opcodes.

## Syntax

```
typedef enum D3DX11_SCAN_OPCODE {
  D3DX11_SCAN_OPCODE_ADD = 1,
  D3DX11_SCAN_OPCODE_MIN,
  D3DX11_SCAN_OPCODE_MAX,
  D3DX11_SCAN_OPCODE_MUL,
  D3DX11_SCAN_OPCODE_AND,
  D3DX11_SCAN_OPCODE_OR,
  D3DX11_SCAN_OPCODE_XOR
} ;
```

## Constants

|  |
| --- |
| `D3DX11_SCAN_OPCODE_ADD` Value: *1* Add values. |
| `D3DX11_SCAN_OPCODE_MIN` Take the minimum value. |
| `D3DX11_SCAN_OPCODE_MAX` Take the maximum value. |
| `D3DX11_SCAN_OPCODE_MUL` Multiply the values. |
| `D3DX11_SCAN_OPCODE_AND` Perform a logical AND on the values. |
| `D3DX11_SCAN_OPCODE_OR` Perform a logical OR on the values. |
| `D3DX11_SCAN_OPCODE_XOR` Perform a logical XOR on the values. |

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