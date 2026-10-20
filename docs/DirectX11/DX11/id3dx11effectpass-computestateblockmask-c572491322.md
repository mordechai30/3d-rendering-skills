Source: [https://learn.microsoft.com/en-us/windows/win32/direct3d11/id3dx11effectpass-computestateblockmask](<https://learn.microsoft.com/en-us/windows/win32/direct3d11/id3dx11effectpass-computestateblockmask>)

# ID3DX11EffectPass::ComputeStateBlockMask method

Generate a mask for allowing/preventing state changes.

## Syntax


```C++
HRESULT ComputeStateBlockMask(
   D3DX11_STATE_BLOCK_MASK *pStateBlockMask
);
```



## Parameters

<dl> <dt>

*pStateBlockMask* 
</dt> <dd>

Type: **[**D3DX11\_STATE\_BLOCK\_MASK**](./d3dx11-state-block-mask-20fbc8f85e.md)\***

A pointer to a state-block mask (see [**D3DX11\_STATE\_BLOCK\_MASK**](./d3dx11-state-block-mask-20fbc8f85e.md)).

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

[ID3DX11EffectPass](./id3dx11effectpass-6c2d5d6dfa.md)
</dt> </dl>