Source: [https://learn.microsoft.com/en-us/windows/win32/direct3d11/d3dx11-group-desc](<https://learn.microsoft.com/en-us/windows/win32/direct3d11/d3dx11-group-desc>)

# D3DX11\_GROUP\_DESC structure

Describes an effect group.

## Syntax


```C++
typedef struct _D3DX11_GROUP_DESC {
  LPCSTR Name;
  UINT   Techniques;
  UINT   Annotations;
} D3DX11_GROUP_DESC;
```



## Members

<dl> <dt>

**Name**
</dt> <dd>

Type: **[**LPCSTR**](/windows/desktop/WinProg/windows-data-types)**

</dd> <dd>

Name of this group (only **NULL** if global).

</dd> <dt>

**Techniques**
</dt> <dd>

Type: **[**UINT**](/windows/desktop/WinProg/windows-data-types)**

</dd> <dd>

Number of techniques contained in group.

</dd> <dt>

**Annotations**
</dt> <dd>

Type: **[**UINT**](/windows/desktop/WinProg/windows-data-types)**

</dd> <dd>

Number of annotations on this group.

</dd> </dl>

## Remarks

D3DX11\_GROUP\_DESC is used with [**ID3DX11EffectTechnique::GetDesc**](./id3dx11effecttechnique-getdesc-6543c44078.md).

## Requirements



| Requirement | Value |
|-------------------|-------------------------------------------------------------------------------------------|
| Header<br/> | <dl> <dt>D3dx11effect.h</dt> </dl> |



## See also

<dl> <dt>

[Effects 11 Structures](./d3d11-graphics-reference-effects11-structures-bcfbef65dd.md)
</dt> </dl>