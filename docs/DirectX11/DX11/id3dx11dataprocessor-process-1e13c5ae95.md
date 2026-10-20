Source: [https://learn.microsoft.com/en-us/windows/win32/direct3d11/id3dx11dataprocessor-process](<https://learn.microsoft.com/en-us/windows/win32/direct3d11/id3dx11dataprocessor-process>)

# ID3DX11DataProcessor::Process method

> [!Note]  
> The D3DX (D3DX 9, D3DX 10, and D3DX 11) utility library is deprecated for Windows 8 and is not supported for Windows Store apps.

 

Processes data.

## Syntax


```C++
HRESULT Process(
  [in] void   *pData,
  [in] SIZE_T cBytes
);
```



## Parameters

<dl> <dt>

*pData* \[in\]
</dt> <dd>

Type: **void\***

Pointer to the data to be processed.

</dd> <dt>

*cBytes* \[in\]
</dt> <dd>

Type: **[**SIZE\_T**](/windows/desktop/WinProg/windows-data-types)**

Size of the data to be processed.

</dd> </dl>

## Return value

Type: **[**HRESULT**](https://msdn.microsoft.com/library/Bb401631(v=MSDN.10).aspx)**

The return value is one of the values listed in [Direct3D 11 Return Codes](./d3d11-graphics-reference-returnvalues-2d2638a6a7.md).

## Remarks

This method is used by an [**ID3DX11ThreadPump Interface**](./id3dx11threadpump-1d47459670.md).

## Requirements



| Requirement | Value |
|--------------------|-----------------------------------------------------------------------------------------|
| Header<br/>  | <dl> <dt>D3DX11core.h</dt> </dl> |
| Library<br/> | <dl> <dt>D3DX11.lib</dt> </dl>   |



## See also

<dl> <dt>

[ID3DX11DataProcessor](./id3dx11dataprocessor-1d7ffa3059.md)
</dt> <dt>

[D3DX Interfaces](./d3d11-graphics-reference-d3dx11-interfaces-bf8653ed03.md)
</dt> </dl>