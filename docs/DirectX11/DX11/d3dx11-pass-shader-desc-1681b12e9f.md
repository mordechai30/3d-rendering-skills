Source: [https://learn.microsoft.com/en-us/windows/win32/direct3d11/d3dx11-pass-shader-desc](<https://learn.microsoft.com/en-us/windows/win32/direct3d11/d3dx11-pass-shader-desc>)

# D3DX11\_PASS\_SHADER\_DESC structure

Describes an effect pass.

## Syntax


```C++
typedef struct _D3DX11_PASS_SHADER_DESC {
  ID3DX11EffectShaderVariable *pShaderVariable;
  UINT                        ShaderIndex;
} D3DX11_PASS_SHADER_DESC;
```



## Members

<dl> <dt>

**pShaderVariable**
</dt> <dd>

Type: **[**ID3DX11EffectShaderVariable**](./id3dx11effectshadervariable-81ab8d90dd.md)\***

</dd> <dd>

The variable that this shader came from.

</dd> <dt>

**ShaderIndex**
</dt> <dd>

Type: **[**UINT**](/windows/desktop/WinProg/windows-data-types)**

</dd> <dd>

The element of pShaderVariable (if an array) or 0 if not applicable.

</dd> </dl>

## Remarks

D3DX11\_PASS\_SHADER\_DESC is used with [**ID3DX11EffectPass**](./id3dx11effectpass-6c2d5d6dfa.md) Get\*ShaderDesc methods.

If this is an inline shader assignment, the returned interface will be an anonymous shader variable, which is not retrievable any other way. It's name in the variable description will be "$Anonymous". If there is no assignment of this type in the pass block, pShaderVariable != **NULL**, but pShaderVariable->IsValid() == **FALSE**.

## Requirements



| Requirement | Value |
|-------------------|-------------------------------------------------------------------------------------------|
| Header<br/> | <dl> <dt>D3dx11effect.h</dt> </dl> |



## See also

<dl> <dt>

[Effects 11 Structures](./d3d11-graphics-reference-effects11-structures-bcfbef65dd.md)
</dt> </dl>