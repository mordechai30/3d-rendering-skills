Source: [https://learn.microsoft.com/en-us/windows/win32/direct3d11/id3dx11threadpump-addworkitem](<https://learn.microsoft.com/en-us/windows/win32/direct3d11/id3dx11threadpump-addworkitem>)

# ID3DX11ThreadPump::AddWorkItem method

> [!Note]  
> The D3DX (D3DX 9, D3DX 10, and D3DX 11) utility library is deprecated for Windows 8 and is not supported for Windows Store apps.

 

Adds a work item to the thread pump.

## Syntax


```C++
HRESULT AddWorkItem(
  [in]  ID3DX11DataLoader    *pDataLoader,
  [in]  ID3DX11DataProcessor *pDataProcessor,
  [in]  HRESULT              *pHResult,
  [out] void                 **ppDeviceObject
);
```



## Parameters

<dl> <dt>

*pDataLoader* \[in\]
</dt> <dd>

Type: **[**ID3DX11DataLoader**](./id3dx11dataloader-ce1de847d8.md)\***

The loader that the thread pump will use when a work item requires data to be loaded.

</dd> <dt>

*pDataProcessor* \[in\]
</dt> <dd>

Type: **[**ID3DX11DataProcessor**](./id3dx11dataprocessor-1d7ffa3059.md)\***

The processor that the thread pump will use when a work item requires data to be processed.

</dd> <dt>

*pHResult* \[in\]
</dt> <dd>

Type: **[**HRESULT**](https://msdn.microsoft.com/library/Bb401631(v=MSDN.10).aspx)\***

A pointer to the return value. May be **NULL**.

</dd> <dt>

*ppDeviceObject* \[out\]
</dt> <dd>

Type: **void\*\***

The device that uses the object.

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

[ID3DX11ThreadPump](./id3dx11threadpump-1d47459670.md)
</dt> <dt>

[D3DX Interfaces](./d3d11-graphics-reference-d3dx11-interfaces-bf8653ed03.md)
</dt> </dl>