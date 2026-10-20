Source: [https://learn.microsoft.com/en-us/windows/win32/direct3d11/d3dx11createthreadpump](<https://learn.microsoft.com/en-us/windows/win32/direct3d11/d3dx11createthreadpump>)

# D3DX11CreateThreadPump function

> [!Note]  
> The D3DX (D3DX 9, D3DX 10, and D3DX 11) utility library is deprecated for Windows 8 and is not supported for Windows Store apps. See Remarks.

 

Create a thread pump.

## Syntax


```C++
HRESULT D3DX11CreateThreadPump(
  _In_  UINT              cIoThreads,
  _In_  UINT              cProcThreads,
  _Out_ ID3DX11ThreadPump **ppThreadPump
);
```



## Parameters

<dl> <dt>

*cIoThreads* \[in\]
</dt> <dd>

Type: **[**UINT**](/windows/desktop/WinProg/windows-data-types)**

The number of I/O threads to create. If 0 is specified, Direct3D will attempt to calculate the optimal number of threads based on the hardware configuration.

</dd> <dt>

*cProcThreads* \[in\]
</dt> <dd>

Type: **[**UINT**](/windows/desktop/WinProg/windows-data-types)**

The number of process threads to create. If 0 is specified, Direct3D will attempt to calculate the optimal number of threads based on the hardware configuration.

</dd> <dt>

*ppThreadPump* \[out\]
</dt> <dd>

Type: **[**ID3DX11ThreadPump**](./id3dx11threadpump-1d47459670.md)\*\***

The created thread pump. See [**ID3DX11ThreadPump Interface**](./id3dx11threadpump-1d47459670.md).

</dd> </dl>

## Return value

Type: **[**HRESULT**](https://msdn.microsoft.com/library/Bb401631(v=MSDN.10).aspx)**

The return value is one of the values listed in [Direct3D 11 Return Codes](./d3d11-graphics-reference-returnvalues-2d2638a6a7.md).

## Remarks

A thread pump is a very resource-intensive object. Only one thread pump should be created per application.

There s no implementation of the  async loader  outside of D3DX 10, and D3DX 11.

For Windows Store apps, the DirectX samples (for example, the [Direct3D tutorial sample](https://github.com/microsoftarchive/msdn-code-gallery-microsoft/tree/master/Official%20Windows%20Platform%20Sample/Direct3D%20tutorial%20sample)) include the **BasicLoader** module that uses the Windows Runtime asynchronous programming model ([**AsyncBase**](/previous-versions/visualstudio/visual-studio-2012/br244878(v=vs.110))).

For Win32 desktop apps, you can use the [Concurrency Runtime](/previous-versions/visualstudio/visual-studio-2010/ee207192(v=vs.100)) to implement something similar to the Windows Runtime asynchronous programming model.

## Requirements



| Requirement | Value |
|--------------------|-----------------------------------------------------------------------------------------|
| Header<br/>  | <dl> <dt>D3DX11core.h</dt> </dl> |
| Library<br/> | <dl> <dt>D3DX11.lib</dt> </dl>   |



## See also

<dl> <dt>

[D3DX Functions](./d3d11-graphics-reference-d3dx11-functions-e9c2bae664.md)
</dt> </dl>