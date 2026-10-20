Source: [https://learn.microsoft.com/en-us/windows/win32/direct3d11/d3dx11-technique-desc](<https://learn.microsoft.com/en-us/windows/win32/direct3d11/d3dx11-technique-desc>)

# D3DX11\_TECHNIQUE\_DESC structure

Describes an effect technique.

## Syntax


```C++
typedef struct _D3DX11_TECHNIQUE_DESC {
  LPCSTR Name;
  UINT   Passes;
  UINT   Annotations;
} D3DX11_TECHNIQUE_DESC;
```



## Members

<dl> <dt>

**Name**
</dt> <dd>

Type: **[**LPCSTR**](/windows/desktop/WinProg/windows-data-types)**

</dd> <dd>

Name of this technique (NULL if not anonymous).

</dd> <dt>

**Passes**
</dt> <dd>

Type: **[**UINT**](/windows/desktop/WinProg/windows-data-types)**

</dd> <dd>

Number of passes contained in the technique.

</dd> <dt>

**Annotations**
</dt> <dd>

Type: **[**UINT**](/windows/desktop/WinProg/windows-data-types)**

</dd> <dd>

Number of annotations on this technique.

</dd> </dl>

## Remarks

D3DX11\_TECHNIQUE\_DESC is used with [**ID3DX11EffectTechnique::GetDesc**](./id3dx11effecttechnique-getdesc-6543c44078.md).

## Requirements



| Requirement | Value |
|-------------------|-------------------------------------------------------------------------------------------|
| Header<br/> | <dl> <dt>D3dx11effect.h</dt> </dl> |



## See also

<dl> <dt>

[Effects 11 Structures](./d3d11-graphics-reference-effects11-structures-bcfbef65dd.md)
</dt> </dl>