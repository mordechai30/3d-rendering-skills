Source: [https://learn.microsoft.com/en-us/windows/win32/direct3d11/id3dx11effectvariable-setrawvalue](<https://learn.microsoft.com/en-us/windows/win32/direct3d11/id3dx11effectvariable-setrawvalue>)

# ID3DX11EffectVariable::SetRawValue method

Set data.

## Syntax


```C++
HRESULT SetRawValue(
   void *pData,
   UINT Offset,
   UINT Count
);
```



## Parameters

<dl> <dt>

*pData* 
</dt> <dd>

Type: **void\***

A pointer to the variable.

</dd> <dt>

*Offset* 
</dt> <dd>

Type: **[**UINT**](/windows/desktop/WinProg/windows-data-types)**

The offset (in bytes) from the beginning of the pointer to the data.

</dd> <dt>

*Count* 
</dt> <dd>

Type: **[**UINT**](/windows/desktop/WinProg/windows-data-types)**

The number of bytes to set.

</dd> </dl>

## Return value

Type: **[**HRESULT**](https://msdn.microsoft.com/library/Bb401631(v=MSDN.10).aspx)**

Returns one of the following [Direct3D 11 Return Codes](./d3d11-graphics-reference-returnvalues-2d2638a6a7.md).

## Remarks

This method does no conversion or type checking; it is therefore a very quick way to access array items.

> [!Note]  
> The DirectX SDK does not supply any compiled binaries for effects. You must use Effects 11 source to build your effects-type application. For more information about using Effects 11 source, see [Differences Between Effects 10 and Effects 11](./d3d11-graphics-programming-guide-effects-differences-f7025c8c69.md).

 

## Requirements



| Requirement | Value |
|--------------------|----------------------------------------------------------------------------------------------------------------------------------------------|
| Header<br/>  | <dl> <dt>D3dx11effect.h</dt> </dl>                                                    |
| Library<br/> | <dl> <dt>N/A (An Effects 11 library is available online as shared source.)</dt> </dl> |



## See also

<dl> <dt>

[ID3DX11EffectVariable](./id3dx11effectvariable-89fd46cf57.md)
</dt> </dl>