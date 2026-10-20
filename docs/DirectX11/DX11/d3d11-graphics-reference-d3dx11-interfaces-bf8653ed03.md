Source: [https://learn.microsoft.com/en-us/windows/win32/direct3d11/d3d11-graphics-reference-d3dx11-interfaces](<https://learn.microsoft.com/en-us/windows/win32/direct3d11/d3d11-graphics-reference-d3dx11-interfaces>)

# D3DX Interfaces (Direct3D 11 Graphics)

This section contains reference information for the component object model (COM) interfaces provided by the D3DX utility library.

> [!Note]  
> The D3DX (D3DX 9, D3DX 10, and D3DX 11) utility library is deprecated for Windows 8 and is not supported for Windows Store apps.

 


## In this section




| Topic | Description | 
|-------|-------------|
| [**ID3DX11DataLoader**](./id3dx11dataloader-ce1de847d8.md)<br> |  **Note:** The D3DX (D3DX 9, D3DX 10, and D3DX 11) utility library is deprecated for Windows 8 and is not supported for Windows Store apps.<br> Data loading object used by [**ID3DX11ThreadPump Interface**](./id3dx11threadpump-1d47459670.md) for loading data asynchronously.<br> | 
| [**ID3DX11DataProcessor**](./id3dx11dataprocessor-1d7ffa3059.md)<br> |  **Note:** The D3DX (D3DX 9, D3DX 10, and D3DX 11) utility library is deprecated for Windows 8 and is not supported for Windows Store apps.<br> Data processing object used by [**ID3DX11ThreadPump Interface**](./id3dx11threadpump-1d47459670.md) for loading data asynchronously.<br> | 
| [**ID3DX11ThreadPump**](./id3dx11threadpump-1d47459670.md)<br> |  **Note:** The D3DX (D3DX 9, D3DX 10, and D3DX 11) utility library is deprecated for Windows 8 and is not supported for Windows Store apps.<br> A thread pump executes tasks asynchronously. It is created by calling [**D3DX11CreateThreadPump**](./d3dx11createthreadpump-a30fb23009.md). There are several APIs that take an optional thread pump as a parameter, such as [**D3DX11CreateTextureFromFile**](./d3dx11createtexturefromfile-0ef1c79cb6.md) and [**D3DX11CompileFromFile**](./d3dx11compilefromfile-2f4f2f35cf.md); if you pass a thread pump interface into these APIs, the functions will execute asynchronously on a separate thread. Particularly on multiprocessor machines, a thread pump can load resources and process data without a noticeable decrease in performance.<br> | 




 

## Related topics

<dl> <dt>

[D3DX 11 Reference](./d3d11-graphics-reference-d3dx11-496260e345.md)
</dt> </dl>