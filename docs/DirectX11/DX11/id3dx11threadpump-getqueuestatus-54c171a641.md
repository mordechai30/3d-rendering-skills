Source: [https://learn.microsoft.com/en-us/windows/win32/direct3d11/id3dx11threadpump-getqueuestatus](<https://learn.microsoft.com/en-us/windows/win32/direct3d11/id3dx11threadpump-getqueuestatus>)

# ID3DX11ThreadPump::GetQueueStatus method

> [!Note]  
> The D3DX (D3DX 9, D3DX 10, and D3DX 11) utility library is deprecated for Windows 8 and is not supported for Windows Store apps.

 

Gets the number of items in each of the three queues inside the thread pump.

## Syntax


```C++
HRESULT GetQueueStatus(
  [in] UINT *pIoQueue,
  [in] UINT *pProcessQueue,
  [in] UINT *pDeviceQueue
);
```



## Parameters

<dl> <dt>

*pIoQueue* \[in\]
</dt> <dd>

Type: **[**UINT**](/windows/desktop/WinProg/windows-data-types)\***

Number of items in the I/O queue.

</dd> <dt>

*pProcessQueue* \[in\]
</dt> <dd>

Type: **[**UINT**](/windows/desktop/WinProg/windows-data-types)\***

Number of items in the process queue.

</dd> <dt>

*pDeviceQueue* \[in\]
</dt> <dd>

Type: **[**UINT**](/windows/desktop/WinProg/windows-data-types)\***

Number of items in the device queue.

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