Source: [https://learn.microsoft.com/en-us/windows/win32/direct3d11/id3dx11effectdepthstencilvariable-setdepthstencilstate](<https://learn.microsoft.com/en-us/windows/win32/direct3d11/id3dx11effectdepthstencilvariable-setdepthstencilstate>)

# ID3DX11EffectDepthStencilVariable::SetDepthStencilState method

Sets the depth stencil state.

## Syntax


```C++
HRESULT SetDepthStencilState(
   UINT                    Index,
   ID3D11DepthStencilState *pDepthStencilState
);
```



## Parameters

<dl> <dt>

*Index* 
</dt> <dd>

Type: **[**UINT**](/windows/desktop/WinProg/windows-data-types)**

Index into an array of depth-stencil interfaces. If there is only one depth-stencil interface, use 0.

</dd> <dt>

*pDepthStencilState* 
</dt> <dd>

Type: **[**ID3D11DepthStencilState**](./nn-d3d11-id3d11depthstencilstate-fa0dcc39cc.md)\***

Pointer to an [**ID3D11DepthStencilState**](./nn-d3d11-id3d11depthstencilstate-fa0dcc39cc.md) interface containing the new depth stencil state.

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

[ID3DX11EffectDepthStencilVariable](./id3dx11effectdepthstencilvariable-a77c0fc1c1.md)
</dt> </dl>