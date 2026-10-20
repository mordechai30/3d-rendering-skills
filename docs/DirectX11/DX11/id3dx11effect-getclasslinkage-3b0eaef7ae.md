Source: [https://learn.microsoft.com/en-us/windows/win32/direct3d11/id3dx11effect-getclasslinkage](<https://learn.microsoft.com/en-us/windows/win32/direct3d11/id3dx11effect-getclasslinkage>)

# ID3DX11Effect::GetClassLinkage method

Gets a class linkage interface.

## Syntax


```C++
ID3D11ClassLinkage* GetClassLinkage();
```



## Parameters

This method has no parameters.

## Return value

Type: **[**ID3D11ClassLinkage**](./nn-d3d11-id3d11classlinkage-1ba2aee983.md)\***

Returns a pointer to an [**ID3D11ClassLinkage**](./nn-d3d11-id3d11classlinkage-1ba2aee983.md) interface.

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