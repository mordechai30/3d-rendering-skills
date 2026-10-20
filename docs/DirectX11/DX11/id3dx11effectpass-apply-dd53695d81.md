Source: [https://learn.microsoft.com/en-us/windows/win32/direct3d11/id3dx11effectpass-apply](<https://learn.microsoft.com/en-us/windows/win32/direct3d11/id3dx11effectpass-apply>)

# ID3DX11EffectPass::Apply method

Set the state contained in a pass to the device.

## Syntax


```C++
HRESULT Apply(
   UINT                Flags,
   ID3D11DeviceContext *pContext
);
```



## Parameters

<dl> <dt>

*Flags* 
</dt> <dd>

Type: **[**UINT**](/windows/desktop/WinProg/windows-data-types)**

Unused.

</dd> <dt>

*pContext* 
</dt> <dd>

Type: **[**ID3D11DeviceContext**](./nn-d3d11-id3d11devicecontext-abe911f651.md)\***

The [**ID3D11DeviceContext**](./nn-d3d11-id3d11devicecontext-abe911f651.md) to apply the pass to.

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