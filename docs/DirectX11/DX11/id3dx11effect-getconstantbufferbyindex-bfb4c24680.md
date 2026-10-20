Source: [https://learn.microsoft.com/en-us/windows/win32/direct3d11/id3dx11effect-getconstantbufferbyindex](<https://learn.microsoft.com/en-us/windows/win32/direct3d11/id3dx11effect-getconstantbufferbyindex>)

# ID3DX11Effect::GetConstantBufferByIndex method

Get a constant buffer by index.

## Syntax


```C++
ID3DX11EffectConstantBuffer* GetConstantBufferByIndex(
   UINT Index
);
```



## Parameters

<dl> <dt>

*Index* 
</dt> <dd>

Type: **[**UINT**](/windows/desktop/WinProg/windows-data-types)**

A zero-based index.

</dd> </dl>

## Return value

Type: **[**ID3DX11EffectConstantBuffer**](./id3dx11effectconstantbuffer-ee6cbea9bf.md)\***

A pointer to a [**ID3DX11EffectConstantBuffer**](./id3dx11effectconstantbuffer-ee6cbea9bf.md).

## Remarks

An effect that contains a variable that will be read/written by an application requires at least one constant buffer. For best performance, an effect should organize variables into one or more constant buffers based on their frequency of update.

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