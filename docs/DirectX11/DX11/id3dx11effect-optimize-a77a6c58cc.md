Source: [https://learn.microsoft.com/en-us/windows/win32/direct3d11/id3dx11effect-optimize](<https://learn.microsoft.com/en-us/windows/win32/direct3d11/id3dx11effect-optimize>)

# ID3DX11Effect::Optimize method

Minimize the amount of memory required for an effect.

## Syntax


```C++
HRESULT Optimize();
```



## Parameters

This method has no parameters.

## Return value

Type: **[**HRESULT**](https://msdn.microsoft.com/library/Bb401631(v=MSDN.10).aspx)**

Returns one of the following [Direct3D 11 Return Codes](./d3d11-graphics-reference-returnvalues-2d2638a6a7.md).

## Remarks

An effect uses memory space two different ways: to store the information required by the runtime to execute an effect, and to store the metadata required to reflect information back to an application using the API. You can minimize the amount of memory required by an effect by calling **ID3DX11Effect::Optimize** which removes the reflection metadata from memory. API methods to read variables will no longer work once reflection data has been removed.

The following methods will fail after Optimize has been called on an effect.

-   [**ID3DX11Effect::GetConstantBufferByIndex**](./id3dx11effect-getconstantbufferbyindex-bfb4c24680.md)
-   [**ID3DX11Effect::GetConstantBufferByName**](./id3dx11effect-getconstantbufferbyname-36365ab9e0.md)
-   [**ID3DX11Effect::GetDesc**](./id3dx11effect-getdesc-3ba5554264.md)
-   [**ID3DX11Effect::GetDevice**](./id3dx11effect-getdevice-37bfc481b5.md)
-   [**ID3DX11Effect::GetTechniqueByIndex**](./id3dx11effect-gettechniquebyindex-8578317c31.md)
-   [**ID3DX11Effect::GetTechniqueByName**](./id3dx11effect-gettechniquebyname-32f1c521b9.md)
-   [**ID3DX11Effect::GetVariableByIndex**](./id3dx11effect-getvariablebyindex-e3c2ca66e3.md)
-   [**ID3DX11Effect::GetVariableByName**](./id3dx11effect-getvariablebyname-7811591028.md)
-   [**ID3DX11Effect::GetVariableBySemantic**](./id3dx11effect-getvariablebysemantic-31901685f7.md)

> [!Note]  
> References retrieved with these methods before calling **ID3DX11Effect::Optimize** are still valid after **ID3DX11Effect::Optimize** is called. This allows the application to get all the variables, techniques, and passes it will use, call Optimize, and then use the effect.

 

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