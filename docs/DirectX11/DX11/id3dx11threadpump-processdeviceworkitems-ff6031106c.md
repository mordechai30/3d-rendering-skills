Source: [https://learn.microsoft.com/en-us/windows/win32/direct3d11/id3dx11threadpump-processdeviceworkitems](<https://learn.microsoft.com/en-us/windows/win32/direct3d11/id3dx11threadpump-processdeviceworkitems>)

# ID3DX11ThreadPump::ProcessDeviceWorkItems method

> [!Note]  
> The D3DX (D3DX 9, D3DX 10, and D3DX 11) utility library is deprecated for Windows 8 and is not supported for Windows Store apps.

 

Sets work items to the device after they have finished loading and processing.

## Syntax


```C++
HRESULT ProcessDeviceWorkItems(
  [in] UINT iWorkItemCount
);
```



## Parameters

<dl> <dt>

*iWorkItemCount* \[in\]
</dt> <dd>

Type: **[**UINT**](/windows/desktop/WinProg/windows-data-types)**

The number of work items to set to the device.

</dd> </dl>

## Return value

Type: **[**HRESULT**](https://msdn.microsoft.com/library/Bb401631(v=MSDN.10).aspx)**

The return value is one of the values listed in [Direct3D 11 Return Codes](./d3d11-graphics-reference-returnvalues-2d2638a6a7.md).

## Remarks

When the thread pump has finished loading and processing a resource or shader, it will hold it in a queue until this API is called, at which point the processed items will be set to the device. This is useful for controlling the amount of processing that is spent on binding resources to the device for each frame.

As an example of how one might use this API, say you are nearing the end of one level in your game and you want to begin preloading the textures, shaders, and other resources for the next level. The thread pump will begin loading, decompressing, and processing the resources and shaders on a separate thread until they are ready to be set to the device, at which point it will leave them in a queue. One may not want to set all the resources and shaders to the device at once because this may cause a noticeable temporary slow down in the game's performance. So, this API could be called once per frame so that only a small number work items would be set to the device on each frame, thereby spreading the work load of binding resources to the device over several frames.

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