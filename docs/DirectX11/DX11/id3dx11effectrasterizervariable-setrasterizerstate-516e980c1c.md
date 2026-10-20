Source: [https://learn.microsoft.com/en-us/windows/win32/direct3d11/id3dx11effectrasterizervariable-setrasterizerstate](<https://learn.microsoft.com/en-us/windows/win32/direct3d11/id3dx11effectrasterizervariable-setrasterizerstate>)

# ID3DX11EffectRasterizerVariable::SetRasterizerState method

Sets the rasterizer state.

## Syntax


```C++
HRESULT SetRasterizerState(
   UINT                  Index,
   ID3D11RasterizerState *pRasterizerState
);
```



## Parameters

<dl> <dt>

*Index* 
</dt> <dd>

Type: **[**UINT**](/windows/desktop/WinProg/windows-data-types)**

Index into an array of rasterizer interfaces. If there is only one rasterizer interface, use 0.

</dd> <dt>

*pRasterizerState* 
</dt> <dd>

Type: **[**ID3D11RasterizerState**](./nn-d3d11-id3d11rasterizerstate-ed57c04764.md)\***

Pointer to an [**ID3D11RasterizerState**](./nn-d3d11-id3d11rasterizerstate-ed57c04764.md) interface.

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

[ID3DX11EffectRasterizerVariable](./id3dx11effectrasterizervariable-134fac5726.md)
</dt> </dl>