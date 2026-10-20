Source: [https://learn.microsoft.com/en-us/windows/win32/direct3d11/id3dx11effectunorderedaccessviewvariable-getunorderedaccessviewarray](<https://learn.microsoft.com/en-us/windows/win32/direct3d11/id3dx11effectunorderedaccessviewvariable-getunorderedaccessviewarray>)

# ID3DX11EffectUnorderedAccessViewVariable::GetUnorderedAccessViewArray method

Get an array of unordered-access-views.

## Syntax


```C++
HRESULT GetUnorderedAccessViewArray(
   ID3D11UnorderedAccessView **ppResources,
   UINT                      Offset,
   UINT                      Count
);
```



## Parameters

<dl> <dt>

*ppResources* 
</dt> <dd>

Type: **[**ID3D11UnorderedAccessView**](./nn-d3d11-id3d11unorderedaccessview-837aae35d2.md)\*\***

Pointer to an [**ID3D11UnorderedAccessView**](./nn-d3d11-id3d11unorderedaccessview-837aae35d2.md) pointer that will be set to the UAV array on return.

</dd> <dt>

*Offset* 
</dt> <dd>

Type: **[**UINT**](/windows/desktop/WinProg/windows-data-types)**

Index of the first interface.

</dd> <dt>

*Count* 
</dt> <dd>

Type: **[**UINT**](/windows/desktop/WinProg/windows-data-types)**

Number of elements in the array.

</dd> </dl>

## Return value

Type: **[**HRESULT**](https://msdn.microsoft.com/library/Bb401631(v=MSDN.10).aspx)**

Returns one of the following [Direct3D 11 Return Codes](./d3d11-graphics-reference-returnvalues-2d2638a6a7.md).

## Remarks

> [!Note]  
> The DirectX SDK does not supply any compiled binaries for effects. You must use Effects 11 source to build your effects-type application. For more information about using Effects 11 source, see [Differences Between Effects 10 and Effects 11](./d3d11-graphics-programming-guide-effects-differences-f7025c8c69.md).

 

## Requirements



| Requirement | Value |
|--------------------|----------------------------------------------------------------------------------------------------------------------------------------------|
| Header<br/>  | <dl> <dt>D3dx11effect.h</dt> </dl>                                                    |
| Library<br/> | <dl> <dt>N/A (An Effects 11 library is available online as shared source.)</dt> </dl> |



## See also

<dl> <dt>

[ID3DX11EffectUnorderedAccessViewVariable](./id3dx11effectunorderedaccessviewvariable-af8945de78.md)
</dt> </dl>