Source: [https://learn.microsoft.com/en-us/windows/win32/direct3d11/d3dx11createeffectfrommemory](<https://learn.microsoft.com/en-us/windows/win32/direct3d11/d3dx11createeffectfrommemory>)

# D3DX11CreateEffectFromMemory function

Creates an effect from a binary effect or file.

## Syntax


```C++
HRESULT D3DX11CreateEffectFromMemory(
   void          *pData,
   SIZE_T        DataLength,
   UINT          FXFlags,
   ID3D11Device  *pDevice,
   ID3DX11Effect **ppEffect
);
```



## Parameters

<dl> <dt>

*pData* 
</dt> <dd>

Type: **void\***

Blob of compiled effect data.

</dd> <dt>

*DataLength* 
</dt> <dd>

Type: **[**SIZE\_T**](/windows/desktop/WinProg/windows-data-types)**

Length of the data blob.

</dd> <dt>

*FXFlags* 
</dt> <dd>

Type: **[**UINT**](/windows/desktop/WinProg/windows-data-types)**

No effect flags exist. Set to zero.

</dd> <dt>

*pDevice* 
</dt> <dd>

Type: **[**ID3D11Device**](./nn-d3d11-id3d11device-6e49ef4b9e.md)\***

Pointer to the [**ID3D11Device**](./nn-d3d11-id3d11device-6e49ef4b9e.md) on which to create Effect resources.

</dd> <dt>

*ppEffect* 
</dt> <dd>

Type: **[**ID3DX11Effect**](./id3dx11effect-277b450b03.md)\*\***

Address of the newly created [**ID3DX11Effect**](./id3dx11effect-277b450b03.md) interface.

</dd> </dl>

## Return value

Type: **[**HRESULT**](https://msdn.microsoft.com/library/Bb401631(v=MSDN.10).aspx)**

The return value is one of the values listed in [Direct3D 11 Return Codes](./d3d11-graphics-reference-returnvalues-2d2638a6a7.md).

## Remarks

> [!Note]  
> You must use [Effects 11 source](https://github.com/Microsoft/FX11) to build your effects-type application. For more info about using Effects 11 source, see [Differences Between Effects 10 and Effects 11](./d3d11-graphics-programming-guide-effects-differences-f7025c8c69.md).

 

## Requirements



| Requirement | Value |
|-------------------|-------------------------------------------------------------------------------------------|
| Header<br/> | <dl> <dt>D3dx11effect.h</dt> </dl> |



## See also

<dl> <dt>

[Effects 11 Functions](./d3d11-graphics-reference-effects11-functions-da6eefaf5f.md)
</dt> </dl>