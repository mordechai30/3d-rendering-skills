Source: [https://learn.microsoft.com/en-us/windows/win32/direct3d11/id3dx11effectblendvariable-setblendstate](<https://learn.microsoft.com/en-us/windows/win32/direct3d11/id3dx11effectblendvariable-setblendstate>)

# ID3DX11EffectBlendVariable::SetBlendState method

Sets an effect's blend-state.

## Syntax


```C++
HRESULT SetBlendState(
   UINT             Index,
   ID3D11BlendState *pBlendState
);
```



## Parameters

<dl> <dt>

*Index* 
</dt> <dd>

Type: **[**UINT**](/windows/desktop/WinProg/windows-data-types)**

Index into an array of blend-state interfaces. If there is only one blend-state interface, use 0.

</dd> <dt>

*pBlendState* 
</dt> <dd>

Type: **[**ID3D11BlendState**](./nn-d3d11-id3d11blendstate-c89e087e23.md)\***

A pointer to an [**ID3D11BlendState**](./nn-d3d11-id3d11blendstate-c89e087e23.md) interface containing the blend-state to set.

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

[ID3DX11EffectBlendVariable](./id3dx11effectblendvariable-1cac3f92ff.md)
</dt> </dl>