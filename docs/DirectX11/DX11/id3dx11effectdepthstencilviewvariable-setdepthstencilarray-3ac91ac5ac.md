Source: [https://learn.microsoft.com/en-us/windows/win32/direct3d11/id3dx11effectdepthstencilviewvariable-setdepthstencilarray](<https://learn.microsoft.com/en-us/windows/win32/direct3d11/id3dx11effectdepthstencilviewvariable-setdepthstencilarray>)

# ID3DX11EffectDepthStencilViewVariable::SetDepthStencilArray method

Set an array of depth-stencil-view resources.

## Syntax


```C++
HRESULT SetDepthStencilArray(
   ID3D11DepthStencilView **ppResources,
   UINT                   Offset,
   UINT                   Count
);
```



## Parameters

<dl> <dt>

*ppResources* 
</dt> <dd>

Type: **[**ID3D11DepthStencilView**](./nn-d3d11-id3d11depthstencilview-6b66908b1e.md)\*\***

A pointer to an array of depth-stencil-view interfaces. See [**ID3D11DepthStencilView**](./nn-d3d11-id3d11depthstencilview-6b66908b1e.md).

</dd> <dt>

*Offset* 
</dt> <dd>

Type: **[**UINT**](/windows/desktop/WinProg/windows-data-types)**

The zero-based array index to set the first interface.

</dd> <dt>

*Count* 
</dt> <dd>

Type: **[**UINT**](/windows/desktop/WinProg/windows-data-types)**

The number of elements in the array.

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

[ID3DX11EffectDepthStencilViewVariable](./id3dx11effectdepthstencilviewvariable-0b6e536a0c.md)
</dt> </dl>