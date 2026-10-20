Source: [https://learn.microsoft.com/en-us/windows/win32/direct3d11/d3dx11-effect-desc](<https://learn.microsoft.com/en-us/windows/win32/direct3d11/d3dx11-effect-desc>)

# D3DX11\_EFFECT\_DESC structure

Describes an effect.

## Syntax


```C++
typedef struct _D3DX11_EFFECT_DESC {
  UINT ConstantBuffers;
  UINT GlobalVariables;
  UINT InterfaceVariables;
  UINT Techniques;
  UINT Groups;
} D3DX11_EFFECT_DESC;
```



## Members

<dl> <dt>

**ConstantBuffers**
</dt> <dd>

Type: **[**UINT**](/windows/desktop/WinProg/windows-data-types)**

</dd> <dd>

Number of constant buffers in this effect.

</dd> <dt>

**GlobalVariables**
</dt> <dd>

Type: **[**UINT**](/windows/desktop/WinProg/windows-data-types)**

</dd> <dd>

Number of global variables in this effect.

</dd> <dt>

**InterfaceVariables**
</dt> <dd>

Type: **[**UINT**](/windows/desktop/WinProg/windows-data-types)**

</dd> <dd>

Number of global interfaces in this effect.

</dd> <dt>

**Techniques**
</dt> <dd>

Type: **[**UINT**](/windows/desktop/WinProg/windows-data-types)**

</dd> <dd>

Number of techniques in this effect.

</dd> <dt>

**Groups**
</dt> <dd>

Type: **[**UINT**](/windows/desktop/WinProg/windows-data-types)**

</dd> <dd>

Number of groups in this effect.

</dd> </dl>

## Remarks

D3DX11\_EFFECT\_DESC is used with [**ID3DX11Effect::GetDesc**](./id3dx11effect-getdesc-3ba5554264.md).

## Requirements



| Requirement | Value |
|-------------------|-------------------------------------------------------------------------------------------|
| Header<br/> | <dl> <dt>D3dx11effect.h</dt> </dl> |



## See also

<dl> <dt>

[Effects 11 Structures](./d3d11-graphics-reference-effects11-structures-bcfbef65dd.md)
</dt> </dl>