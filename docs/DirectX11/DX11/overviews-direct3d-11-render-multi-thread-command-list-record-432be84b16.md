Source: [https://learn.microsoft.com/en-us/windows/win32/direct3d11/overviews-direct3d-11-render-multi-thread-command-list-record](<https://learn.microsoft.com/en-us/windows/win32/direct3d11/overviews-direct3d-11-render-multi-thread-command-list-record>)

# How to: Record a Command List

A [command list](./overviews-direct3d-11-render-multi-thread-command-list-e1b0cabde9.md) is a recorded list of rendering commands. This topic shows how to create and record a [command list](./overviews-direct3d-11-render-multi-thread-command-list-e1b0cabde9.md). Use a command list to record render commands and play them back later. A command list is convenient for splitting rendering tasks between threads.

**To record a command list**

1.  A command list must be created from a deferred context, which contains device state and rendering actions. Given a device, create a deferred context by calling [**ID3D11Device::CreateDeferredContext**](./nf-d3d11-id3d11device-createdeferredcontext-2d9c0ea4a7.md).

    ```
    HRESULT hr;
    ID3D11DeviceContext* pDeferredContext = NULL;

    hr = g_pd3dDevice->CreateDeferredContext(0, &pDeferredContext);
    ```

    

2.  Use the deferred context to render.

    ```
    float ClearColor[4] = { 0.0f, 0.125f, 0.3f, 1.0f };
    pDeferredContext->ClearRenderTargetView( g_pRenderTargetView, ClearColor );
        
    // Add additional rendering commands
    ...
    ```

    

    This simple example clears a render target, but you could add additional render commands.

3.  Create/record a command list by calling [**ID3D11DeviceContext::FinishCommandList**](./nf-d3d11-id3d11devicecontext-finishcommandlist-7376c0c5ec.md) and passing a pointer to an uninitialized [**ID3D11CommandList**](./nn-d3d11-id3d11commandlist-2848a61bff.md) interface.

    ```
    ID3D11CommandList* pd3dCommandList = NULL;
    HRESULT hr;
    hr = pDeferredContext->FinishCommandList(FALSE, &pd3dCommandList);
    ```

    

    When the method returns, a command list is created containing all the render commands and an interface is returned to the application.

    The boolean parameter tells the runtime what to do with the pipeline state in the deferred context. **TRUE** means restore the state of the device context to its pre-command list condition when recording is completed, **FALSE** means do not change the state after recording. This means that the device context will reflect the state changes contained in the command list.

To see an example for playing back a command list, see [How to: Play Back a Command List](./overviews-direct3d-11-render-multi-thread-command-list-play-b6b869da03.md).

## Related topics

<dl> <dt>

[Command List](./overviews-direct3d-11-render-multi-thread-command-list-e1b0cabde9.md)
</dt> <dt>

[How to Use Direct3D 11](./how-to-use-direct3d-11-112ea0ccbf.md)
</dt> </dl>