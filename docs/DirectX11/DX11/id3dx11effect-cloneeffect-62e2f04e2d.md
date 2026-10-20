Source: [https://learn.microsoft.com/en-us/windows/win32/direct3d11/id3dx11effect-cloneeffect](<https://learn.microsoft.com/en-us/windows/win32/direct3d11/id3dx11effect-cloneeffect>)

# ID3DX11Effect::CloneEffect method

Creates a copy of an effect interface.

## Syntax


```C++
HRESULT CloneEffect(
   UINT          Flags,
   ID3DX11Effect **ppClonedEffect
);
```



## Parameters

<dl> <dt>

*Flags* 
</dt> <dd>

Type: **[**UINT**](/windows/desktop/WinProg/windows-data-types)**

Flags affecting the creation of the cloned effect. Can be 0 or one of the following values.



| Flag                                    | Description                                                                                                                                      |
|-----------------------------------------|--------------------------------------------------------------------------------------------------------------------------------------------------|
| D3DX11\_EFFECT\_CLONE\_FORCE\_NONSINGLE | Ignore all "single" qualifiers on cbuffers. All cbuffers will have their own [**ID3D11Buffer**](./nn-d3d11-id3d11buffer-0e4ba9908b.md)s created in the cloned effect. |



 

</dd> <dt>

*ppClonedEffect* 
</dt> <dd>

Type: **[**ID3DX11Effect**](./id3dx11effect-277b450b03.md)\*\***

Pointer to an [**ID3DX11Effect**](./id3dx11effect-277b450b03.md) pointer that will be set to the copy of the effect.

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

[ID3DX11Effect](./id3dx11effect-277b450b03.md)
</dt> </dl>