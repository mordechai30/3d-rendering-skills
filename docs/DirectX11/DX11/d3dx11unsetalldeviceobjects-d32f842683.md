Source: [https://learn.microsoft.com/en-us/windows/win32/direct3d11/d3dx11unsetalldeviceobjects](<https://learn.microsoft.com/en-us/windows/win32/direct3d11/d3dx11unsetalldeviceobjects>)

# D3DX11UnsetAllDeviceObjects function

> [!Note]  
> The D3DX (D3DX 9, D3DX 10, and D3DX 11) utility library is deprecated for Windows 8 and is not supported for Windows Store apps.

 

> [!Note]  
> Instead of using this function, we recommend that you use the [**ID3D11DeviceContext::ClearState**](./nf-d3d11-id3d11devicecontext-clearstate-d16437b0ff.md) method.

 

Removes all resources from the device by setting their pointers to **NULL**. This should be called during shutdown of your application. It helps ensure that when one is releasing all of their resources that none of them are bound to the device.

## Syntax


```C++
HRESULT D3DX11UnsetAllDeviceObjects(
  _In_ ID3D11DeviceContext *pContext
);
```



## Parameters

<dl> <dt>

*pContext* \[in\]
</dt> <dd>

Type: **[**ID3D11DeviceContext**](./nn-d3d11-id3d11devicecontext-abe911f651.md)\***

Pointer to an [**ID3D11DeviceContext**](./nn-d3d11-id3d11devicecontext-abe911f651.md) object.

</dd> </dl>

## Return value

Type: **[**HRESULT**](https://msdn.microsoft.com/library/Bb401631(v=MSDN.10).aspx)**

The return value is one of the values listed in [Direct3D 11 Return Codes](./d3d11-graphics-reference-returnvalues-2d2638a6a7.md).

## Requirements



| Requirement | Value |
|--------------------|-----------------------------------------------------------------------------------------|
| Header<br/>  | <dl> <dt>D3DX11core.h</dt> </dl> |
| Library<br/> | <dl> <dt>D3DX11.lib</dt> </dl>   |



## See also

<dl> <dt>

[D3DX Functions](./d3d11-graphics-reference-d3dx11-functions-e9c2bae664.md)
</dt> </dl>