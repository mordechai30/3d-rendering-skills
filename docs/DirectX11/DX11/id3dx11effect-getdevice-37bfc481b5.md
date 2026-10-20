Source: [https://learn.microsoft.com/en-us/windows/win32/direct3d11/id3dx11effect-getdevice](<https://learn.microsoft.com/en-us/windows/win32/direct3d11/id3dx11effect-getdevice>)

# ID3DX11Effect::GetDevice method

Get the device that created the effect.

## Syntax


```C++
HRESULT GetDevice(
   ID3D11Device **ppDevice
);
```



## Parameters

<dl> <dt>

*ppDevice* 
</dt> <dd>

Type: **[**ID3D11Device**](./nn-d3d11-id3d11device-6e49ef4b9e.md)\*\***

A pointer to an [**ID3D11Device**](./nn-d3d11-id3d11device-6e49ef4b9e.md).

</dd> </dl>

## Return value

Type: **[**HRESULT**](https://msdn.microsoft.com/library/Bb401631(v=MSDN.10).aspx)**

Returns one of the following [Direct3D 11 Return Codes](./d3d11-graphics-reference-returnvalues-2d2638a6a7.md).

## Remarks

An effect is created for a specific device, by calling a function such as [**D3DX11CreateEffectFromMemory**](./d3dx11createeffectfrommemory-4ed7004121.md).

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