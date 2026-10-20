Source: [https://learn.microsoft.com/en-us/windows/win32/direct3d11/d3dx11-pass-desc](<https://learn.microsoft.com/en-us/windows/win32/direct3d11/d3dx11-pass-desc>)

# D3DX11\_PASS\_DESC structure

Describes an effect pass, which contains pipeline state.

## Syntax


```C++
typedef struct _D3DX11_PASS_DESC {
  LPCSTR Name;
  UINT   Annotations;
  BYTE   *pIAInputSignature;
  SIZE_T IAInputSignatureSize;
  UINT   StencilRef;
  UINT   SampleMask;
  FLOAT  BlendFactor[4];
} D3DX11_PASS_DESC;
```



## Members

<dl> <dt>

**Name**
</dt> <dd>

Type: **[**LPCSTR**](/windows/desktop/WinProg/windows-data-types)**

</dd> <dd>

Name of this pass (**NULL** if not anonymous).

</dd> <dt>

**Annotations**
</dt> <dd>

Type: **[**UINT**](/windows/desktop/WinProg/windows-data-types)**

</dd> <dd>

Number of annotations on this pass.

</dd> <dt>

**pIAInputSignature**
</dt> <dd>

Type: **[**BYTE**](/windows/desktop/WinProg/windows-data-types)\***

</dd> <dd>

Signature from the vertex shader or geometry shader (if there is no vertex shader) or **NULL** if neither exists.

</dd> <dt>

**IAInputSignatureSize**
</dt> <dd>

Type: **[**SIZE\_T**](/windows/desktop/WinProg/windows-data-types)**

</dd> <dd>

Singature size in bytes.

</dd> <dt>

**StencilRef**
</dt> <dd>

Type: **[**UINT**](/windows/desktop/WinProg/windows-data-types)**

</dd> <dd>

The stencil-reference value used in the depth-stencil state.

</dd> <dt>

**SampleMask**
</dt> <dd>

Type: **[**UINT**](/windows/desktop/WinProg/windows-data-types)**

</dd> <dd>

The sample mask for the blend state.

</dd> <dt>

**BlendFactor**
</dt> <dd>

Type: **[**FLOAT**](/windows/desktop/WinProg/windows-data-types)**

</dd> <dd>

The per-component blend factors (RGBA) for the blend state.

</dd> </dl>

## Remarks

D3DX11\_PASS\_DESC is used with [**ID3DX11EffectPass::GetDesc**](./id3dx11effectpass-getdesc-ba903790ee.md).

## Requirements



| Requirement | Value |
|-------------------|-------------------------------------------------------------------------------------------|
| Header<br/> | <dl> <dt>D3dx11effect.h</dt> </dl> |



## See also

<dl> <dt>

[Effects 11 Structures](./d3d11-graphics-reference-effects11-structures-bcfbef65dd.md)
</dt> </dl>