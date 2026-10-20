Source: [https://learn.microsoft.com/en-us/windows/win32/direct3d11/id3dx11effect-getvariablebysemantic](<https://learn.microsoft.com/en-us/windows/win32/direct3d11/id3dx11effect-getvariablebysemantic>)

# ID3DX11Effect::GetVariableBySemantic method

Get a variable by semantic.

## Syntax


```C++
ID3DX11EffectVariable* GetVariableBySemantic(
   LPCSTR Semantic
);
```



## Parameters

<dl> <dt>

*Semantic* 
</dt> <dd>

Type: **[**LPCSTR**](/windows/desktop/WinProg/windows-data-types)**

The semantic name.

</dd> </dl>

## Return value

Type: **[**ID3DX11EffectVariable**](./id3dx11effectvariable-89fd46cf57.md)\***

A pointer to the effect variable indicated by the Semantic. See [**ID3DX11EffectVariable**](./id3dx11effectvariable-89fd46cf57.md).

## Remarks

Each effect variable can have a semantic attached, which is a user defined metadata string. Some [system-value semantics](/windows/desktop/direct3dhlsl/dx-graphics-hlsl-semantics) are reserved words that trigger built in functionality by pipeline stages.

The method returns a pointer to an [**effect-variable interface**](./id3dx11effectvariable-89fd46cf57.md) if a variable is not found; you can call [**ID3DX11Effect::IsValid**](./id3dx11effect-isvalid-ea812df756.md) to verify whether or not the semantic exists.

> [!Note]  
> The DirectX SDK does not supply any compiled binaries for effects. You must use Effects 11 source to build your effects-type application. For more information about using Effects 11 source, see [Differences Between Effects 10 and Effects 11](./d3d11-graphics-programming-guide-effects-differences-f7025c8c69.md).

 

## Requirements



| Requirement | Value |
|--------------------|----------------------------------------------------------------------------------------------------------------------------------------------|
| Header<br/>  | <dl> <dt>D3dx11effect.h</dt> </dl>                                                    |
| Library<br/> | <dl> <dt>N/A (An Effects 11 library is available online as shared source.)</dt> </dl> |



## See also

<dl> <dt>

[ID3DX11Effect](./id3dx11effect-277b450b03.md)
</dt> </dl>