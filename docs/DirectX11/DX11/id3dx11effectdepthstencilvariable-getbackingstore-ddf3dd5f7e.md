Source: [https://learn.microsoft.com/en-us/windows/win32/direct3d11/id3dx11effectdepthstencilvariable-getbackingstore](<https://learn.microsoft.com/en-us/windows/win32/direct3d11/id3dx11effectdepthstencilvariable-getbackingstore>)

# ID3DX11EffectDepthStencilVariable::GetBackingStore method

Get a pointer to a variable that contains depth-stencil state.

## Syntax


```C++
HRESULT GetBackingStore(
   UINT                     Index,
   D3D11_DEPTH_STENCIL_DESC *pDepthStencilDesc
);
```



## Parameters

<dl> <dt>

*Index* 
</dt> <dd>

Type: **[**UINT**](/windows/desktop/WinProg/windows-data-types)**

Index into an array of depth-stencil-state descriptions. If there is only one depth-stencil variable in the effect, use 0.

</dd> <dt>

*pDepthStencilDesc* 
</dt> <dd>

Type: **[**D3D11\_DEPTH\_STENCIL\_DESC**](./ns-d3d11-d3d11_depth_stencil_desc-e5f1b30def.md)\***

A pointer to a depth-stencil-state description (see [**D3D11\_DEPTH\_STENCIL\_DESC**](./ns-d3d11-d3d11_depth_stencil_desc-e5f1b30def.md)).

</dd> </dl>

## Return value

Type: **[**HRESULT**](https://msdn.microsoft.com/library/Bb401631(v=MSDN.10).aspx)**

Returns one of the following [Direct3D 11 Return Codes](./d3d11-graphics-reference-returnvalues-2d2638a6a7.md).

## Remarks

Effect variables are saved in memory in the backing store; when a technique is applied, the values in the backing store are copied to the device. Backing store data can used to recreate the variable when necessary.

> [!Note]  
> The DirectX SDK does not supply any compiled binaries for effects. You must use Effects 11 source to build your effects-type application. For more information about using Effects 11 source, see [Differences Between Effects 10 and Effects 11](./d3d11-graphics-programming-guide-effects-differences-f7025c8c69.md).

 

## Requirements



| Requirement | Value |
|--------------------|----------------------------------------------------------------------------------------------------------------------------------------------|
| Header<br/>  | <dl> <dt>D3dx11effect.h</dt> </dl>                                                    |
| Library<br/> | <dl> <dt>N/A (An Effects 11 library is available online as shared source.)</dt> </dl> |



## See also

<dl> <dt>

[ID3DX11EffectDepthStencilVariable](./id3dx11effectdepthstencilvariable-a77c0fc1c1.md)
</dt> </dl>