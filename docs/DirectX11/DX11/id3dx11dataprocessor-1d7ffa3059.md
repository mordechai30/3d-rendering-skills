Source: [https://learn.microsoft.com/en-us/windows/win32/direct3d11/id3dx11dataprocessor](<https://learn.microsoft.com/en-us/windows/win32/direct3d11/id3dx11dataprocessor>)

# ID3DX11DataProcessor interface

> [!Note]  
> The D3DX (D3DX 9, D3DX 10, and D3DX 11) utility library is deprecated for Windows 8 and is not supported for Windows Store apps.

 

Data processing object used by [**ID3DX11ThreadPump Interface**](./id3dx11threadpump-1d47459670.md) for loading data asynchronously.

## Members

The **ID3DX11DataProcessor** interface inherits from the [**IUnknown**](/windows/desktop/api/unknwn/nn-unknwn-iunknown) interface. **ID3DX11DataProcessor** also has these types of members:

-   [Methods](#methods)

### Methods

The **ID3DX11DataProcessor** interface has these methods.




| Method | Description | 
|--------|-------------|
| [**CreateDeviceObject**](./id3dx11dataprocessor-createdeviceobject-6e8f82e25d.md) |  **Note:** The D3DX (D3DX 9, D3DX 10, and D3DX 11) utility library is deprecated for Windows 8 and is not supported for Windows Store apps.<br> Creates a device object.<br> | 
| [**Destroy**](./id3dx11dataprocessor-destroy-33e2c9d0dd.md) |  **Note:** The D3DX (D3DX 9, D3DX 10, and D3DX 11) utility library is deprecated for Windows 8 and is not supported for Windows Store apps.<br> Destroys the processor after a work item completes.<br> | 
| [**Process**](./id3dx11dataprocessor-process-1e13c5ae95.md) |  **Note:** The D3DX (D3DX 9, D3DX 10, and D3DX 11) utility library is deprecated for Windows 8 and is not supported for Windows Store apps.<br> Processes data.<br> | 




 

## Remarks

This object can be inherited and its members redefined for processing custom file formats.

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