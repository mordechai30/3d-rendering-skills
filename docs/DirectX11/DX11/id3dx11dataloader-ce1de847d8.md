Source: [https://learn.microsoft.com/en-us/windows/win32/direct3d11/id3dx11dataloader](<https://learn.microsoft.com/en-us/windows/win32/direct3d11/id3dx11dataloader>)

# ID3DX11DataLoader interface

> [!Note]  
> The D3DX (D3DX 9, D3DX 10, and D3DX 11) utility library is deprecated for Windows 8 and is not supported for Windows Store apps.

 

Data loading object used by [**ID3DX11ThreadPump Interface**](./id3dx11threadpump-1d47459670.md) for loading data asynchronously.

## Members

The **ID3DX11DataLoader** interface inherits from the [**IUnknown**](/windows/desktop/api/unknwn/nn-unknwn-iunknown) interface. **ID3DX11DataLoader** also has these types of members:

-   [Methods](#methods)

### Methods

The **ID3DX11DataLoader** interface has these methods.




| Method | Description | 
|--------|-------------|
| [**Decompress**](./id3dx11dataloader-decompress-0e204f69eb.md) |  **Note:** The D3DX (D3DX 9, D3DX 10, and D3DX 11) utility library is deprecated for Windows 8 and is not supported for Windows Store apps.<br> Decompresses encoded data.<br> | 
| [**Destroy**](./id3dx11dataloader-destroy-f68d3b2be3.md) |  **Note:** The D3DX (D3DX 9, D3DX 10, and D3DX 11) utility library is deprecated for Windows 8 and is not supported for Windows Store apps.<br> Destroys the loader after a work item completes.<br> | 
| [**Load**](./id3dx11dataloader-load-ddd999cb05.md) |  **Note:** The D3DX (D3DX 9, D3DX 10, and D3DX 11) utility library is deprecated for Windows 8 and is not supported for Windows Store apps.<br> Loads data from a disk.<br> | 




 

## Remarks

This object can be inherited and its members redefined. Doing so would enable you to customize the API for loading and decompressing your own custom file formats.

## Requirements



| Requirement | Value |
|-------------------------------------|-----------------------------------------------------------------------------------------|
| Minimum supported client<br/> | Windows 7 \[desktop apps only\]<br/>                                              |
| Minimum supported server<br/> | Windows Server 2008 R2 \[desktop apps only\]<br/>                                 |
| Header<br/>                   | <dl> <dt>D3DX11core.h</dt> </dl> |
| Library<br/>                  | <dl> <dt>D3DX11.lib</dt> </dl>   |



## See also

<dl> <dt>

[D3DX Interfaces](./d3d11-graphics-reference-d3dx11-interfaces-bf8653ed03.md)
</dt> </dl>