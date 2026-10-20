Source: [https://learn.microsoft.com/en-us/windows/win32/direct3d11/id3dx11effect-getvariablebyname](<https://learn.microsoft.com/en-us/windows/win32/direct3d11/id3dx11effect-getvariablebyname>)

# ID3DX11Effect::GetVariableByName method

Get a variable by name.

## Syntax


```C++
ID3DX11EffectVariable* GetVariableByName(
   LPCSTR Name
);
```



## Parameters

<dl> <dt>

*Name* 
</dt> <dd>

Type: **[**LPCSTR**](/windows/desktop/WinProg/windows-data-types)**

The variable name.

</dd> </dl>

## Return value

Type: **[**ID3DX11EffectVariable**](./id3dx11effectvariable-89fd46cf57.md)\***

A pointer to an [**ID3DX11EffectVariable**](./id3dx11effectvariable-89fd46cf57.md). Returns an invalid variable if the specified name cannot be found.

## Remarks

An effect may contain one or more variables. Variables outside of a technique are considered global to all effects, those located inside of a technique are local to that technique. You can access an effect variable using its name or with an index.

The method returns a pointer to an [**effect-variable interface**](./id3dx11effectvariable-89fd46cf57.md) whether or not a variable is found. [**ID3DX11Effect::IsValid**](./id3dx11effect-isvalid-ea812df756.md) should be called to verify whether or not the name exists.

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