Source: [https://learn.microsoft.com/en-us/windows/win32/direct3d11/id3dx11effectmatrixvariable-getmatrixtranspose](<https://learn.microsoft.com/en-us/windows/win32/direct3d11/id3dx11effectmatrixvariable-getmatrixtranspose>)

# ID3DX11EffectMatrixVariable::GetMatrixTranspose method

Transpose and get a floating-point matrix.

## Syntax


```C++
HRESULT GetMatrixTranspose(
   float *pData
);
```



## Parameters

<dl> <dt>

*pData* 
</dt> <dd>

Type: **float\***

A pointer to the first element of a transposed matrix.

</dd> </dl>

## Return value

Type: **[**HRESULT**](https://msdn.microsoft.com/library/Bb401631(v=MSDN.10).aspx)**

Returns one of the following [Direct3D 11 Return Codes](./d3d11-graphics-reference-returnvalues-2d2638a6a7.md).

## Remarks

Transposing a matrix will rearrange the data order from row-column order to column-row order (or vice versa).

> [!Note]  
> The DirectX SDK does not supply any compiled binaries for effects. You must use Effects 11 source to build your effects-type application. For more information about using Effects 11 source, see [Differences Between Effects 10 and Effects 11](./d3d11-graphics-programming-guide-effects-differences-f7025c8c69.md).

 

## Requirements



| Requirement | Value |
|--------------------|----------------------------------------------------------------------------------------------------------------------------------------------|
| Header<br/>  | <dl> <dt>D3dx11effect.h</dt> </dl>                                                    |
| Library<br/> | <dl> <dt>N/A (An Effects 11 library is available online as shared source.)</dt> </dl> |



## See also

<dl> <dt>

[ID3DX11EffectMatrixVariable](./id3dx11effectmatrixvariable-2bcd48d5b8.md)
</dt> </dl>