Source: [https://learn.microsoft.com/en-us/windows/win32/direct3d11/d3dx11-effect-type-desc](<https://learn.microsoft.com/en-us/windows/win32/direct3d11/d3dx11-effect-type-desc>)

# D3DX11\_EFFECT\_TYPE\_DESC structure

Describes an effect-variable type.

## Syntax


```C++
typedef struct _D3DX11_EFFECT_TYPE_DESC {
  LPCSTR                      TypeName;
  D3D10_SHADER_VARIABLE_CLASS Class;
  D3D10_SHADER_VARIABLE_TYPE  Type;
  UINT                        Elements;
  UINT                        Members;
  UINT                        Rows;
  UINT                        Columns;
  UINT                        PackedSize;
  UINT                        UnpackedSize;
  UINT                        Stride;
} D3DX11_EFFECT_TYPE_DESC;
```



## Members

<dl> <dt>

**TypeName**
</dt> <dd>

Type: **[**LPCSTR**](/windows/desktop/WinProg/windows-data-types)**

</dd> <dd>

Name of the type, for example "float4" or "MyStruct".

</dd> <dt>

**Class**
</dt> <dd>

Type: **[**D3D10\_SHADER\_VARIABLE\_CLASS**](./ne-d3dcommon-d3d_shader_variable_class-bfddf6e870.md)**

</dd> <dd>

The variable class (see [**D3D10\_SHADER\_VARIABLE\_CLASS**](./ne-d3dcommon-d3d_shader_variable_class-bfddf6e870.md)).

</dd> <dt>

**Type**
</dt> <dd>

Type: **[**D3D10\_SHADER\_VARIABLE\_TYPE**](./ne-d3dcommon-d3d_shader_variable_type-17113ddcc0.md)**

</dd> <dd>

The variable type (see [**D3D10\_SHADER\_VARIABLE\_TYPE**](./ne-d3dcommon-d3d_shader_variable_type-17113ddcc0.md)).

</dd> <dt>

**Elements**
</dt> <dd>

Type: **[**UINT**](/windows/desktop/WinProg/windows-data-types)**

</dd> <dd>

Number of elements in this type (0 if not an array).

</dd> <dt>

**Members**
</dt> <dd>

Type: **[**UINT**](/windows/desktop/WinProg/windows-data-types)**

</dd> <dd>

Number of members (0 if not a structure).

</dd> <dt>

**Rows**
</dt> <dd>

Type: **[**UINT**](/windows/desktop/WinProg/windows-data-types)**

</dd> <dd>

Number of rows in this type (0 if not a numeric primitive).

</dd> <dt>

**Columns**
</dt> <dd>

Type: **[**UINT**](/windows/desktop/WinProg/windows-data-types)**

</dd> <dd>

Number of columns in this type (0 if not a numeric primitive).

</dd> <dt>

**PackedSize**
</dt> <dd>

Type: **[**UINT**](/windows/desktop/WinProg/windows-data-types)**

</dd> <dd>

Number of bytes required to represent this data type, when tightly packed.

</dd> <dt>

**UnpackedSize**
</dt> <dd>

Type: **[**UINT**](/windows/desktop/WinProg/windows-data-types)**

</dd> <dd>

Number of bytes occupied by this data type, when laid out in a constant buffer.

</dd> <dt>

**Stride**
</dt> <dd>

Type: **[**UINT**](/windows/desktop/WinProg/windows-data-types)**

</dd> <dd>

Number of bytes to seek between elements, when laid out in a constant buffer.

</dd> </dl>

## Remarks

D3DX11\_EFFECT\_TYPE\_DESC is used with [**ID3DX11EffectType::GetDesc**](./id3dx11effecttype-getdesc-5c6cd0fda2.md)

## Requirements



| Requirement | Value |
|-------------------|-------------------------------------------------------------------------------------------|
| Header<br/> | <dl> <dt>D3dx11effect.h</dt> </dl> |



## See also

<dl> <dt>

[Effects 11 Structures](./d3d11-graphics-reference-effects11-structures-bcfbef65dd.md)
</dt> </dl>