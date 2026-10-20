Source: [https://learn.microsoft.com/en-us/windows/win32/direct3d11/overviews-direct3d-11-devices-get-adapter-info](<https://learn.microsoft.com/en-us/windows/win32/direct3d11/overviews-direct3d-11-devices-get-adapter-info>)

# How To: Get Adapter Display Modes

This topic shows how to use Microsoft DirectX Graphics Infrastructure (DXGI) to get the valid display modes associated with an adapter. DirectX 10 and 11 can use DXGI to get the valid display modes. Knowing the valid display modes ensures that your application can properly choose a valid full-screen mode.

**To get adapter display modes**

1.  Create an [**IDXGIFactory**](/windows/desktop/api/dxgi/nn-dxgi-idxgifactory) object and use it to enumerate the available adapters. For more information, see [How To: Enumerate Adapters](./overviews-direct3d-11-devices-enum-36035cb71a.md).
2.  Call IDXGIAdapter::EnumOutputs to enumerate the outputs for each adapter.
    ```
    IDXGIOutput* pOutput = NULL; 
    HRESULT hr;

    hr = pAdapter->EnumOutputs(0,&pOutput);
    ```

    

3.  Call IDXGIOutput::GetDisplayModeList to retrieve an array of [**DXGI\_MODE\_DESC**](/previous-versions/windows/desktop/legacy/bb173064(v=vs.85)) structures and the number of elements in the array. Each **DXGI\_MODE\_DESC** structure represents a valid display mode for the output.
    ```
    UINT numModes = 0;
    DXGI_MODE_DESC* displayModes = NULL;
    DXGI_FORMAT format = DXGI_FORMAT_R32G32B32A32_FLOAT;

        // Get the number of elements
        hr = pOutput->GetDisplayModeList( format, 0, &numModes, NULL);

        displayModes = new DXGI_MODE_DESC[numModes]; 

        // Get the list
        hr = pOutput->GetDisplayModeList( format, 0, &numModes, displayModes);
    ```

    

## Related topics

<dl> <dt>

[Devices](./overviews-direct3d-11-devices-8464b8d294.md)
</dt> <dt>

[How to Use Direct3D 11](./how-to-use-direct3d-11-112ea0ccbf.md)
</dt> </dl>