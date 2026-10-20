Source: [https://learn.microsoft.com/en-us/windows/win32/direct3d11/id3dx11effectinterfacevariable-setclassinstance](<https://learn.microsoft.com/en-us/windows/win32/direct3d11/id3dx11effectinterfacevariable-setclassinstance>)

# ID3DX11EffectInterfaceVariable::SetClassInstance method

Sets a class instance.

## Syntax


```C++
HRESULT SetClassInstance(
   ID3DX11EffectClassInstanceVariable *pEffectClassInstance
);
```



## Parameters

<dl> <dt>

*pEffectClassInstance* 
</dt> <dd>

Type: **[**ID3DX11EffectClassInstanceVariable**](./id3dx11effectclassinstancevariable-7764ee39f2.md)\***

Pointer to an [**ID3DX11EffectClassInstanceVariable**](./id3dx11effectclassinstancevariable-7764ee39f2.md) interface.

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

[ID3DX11EffectInterfaceVariable](./id3dx11effectinterfacevariable-ee6aee853e.md)
</dt> </dl>