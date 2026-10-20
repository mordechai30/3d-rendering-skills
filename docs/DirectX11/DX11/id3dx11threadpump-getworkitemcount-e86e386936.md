Source: [https://learn.microsoft.com/en-us/windows/win32/direct3d11/id3dx11threadpump-getworkitemcount](<https://learn.microsoft.com/en-us/windows/win32/direct3d11/id3dx11threadpump-getworkitemcount>)

# ID3DX11ThreadPump::GetWorkItemCount method

> [!Note]  
> The D3DX (D3DX 9, D3DX 10, and D3DX 11) utility library is deprecated for Windows 8 and is not supported for Windows Store apps.

 

Gets the number of work items in the thread pump.

## Syntax


```C++
UINT GetWorkItemCount();
```



## Parameters

This method has no parameters.

## Return value

Type: **[**UINT**](/windows/desktop/WinProg/windows-data-types)**

The number of work items queued in the thread pump.

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