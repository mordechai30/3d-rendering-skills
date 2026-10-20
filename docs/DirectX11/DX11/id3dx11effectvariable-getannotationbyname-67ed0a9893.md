Source: [https://learn.microsoft.com/en-us/windows/win32/direct3d11/id3dx11effectvariable-getannotationbyname](<https://learn.microsoft.com/en-us/windows/win32/direct3d11/id3dx11effectvariable-getannotationbyname>)

# ID3DX11EffectVariable::GetAnnotationByName method

Get an annotation by name.

## Syntax


```C++
ID3DX11EffectVariable* GetAnnotationByName(
   LPCSTR Name
);
```



## Parameters

<dl> <dt>

*Name* 
</dt> <dd>

Type: **[**LPCSTR**](/windows/desktop/WinProg/windows-data-types)**

The annotation name.

</dd> </dl>

## Return value

Type: **[**ID3DX11EffectVariable**](./id3dx11effectvariable-89fd46cf57.md)\***

A pointer to an [**ID3DX11EffectVariable**](./id3dx11effectvariable-89fd46cf57.md). Note that if the annotation is not found the **ID3DX11EffectVariable** returned will be empty. The [**ID3DX11EffectVariable::IsValid**](./id3dx11effectvariable-isvalid-c0ad788b13.md) method should be called to determine whether the annotation was found.

## Remarks

Annonations can be attached to a technique, a pass, or a global variable.

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