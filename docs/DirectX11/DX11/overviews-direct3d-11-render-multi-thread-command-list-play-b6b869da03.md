Source: [https://learn.microsoft.com/en-us/windows/win32/direct3d11/overviews-direct3d-11-render-multi-thread-command-list-play](<https://learn.microsoft.com/en-us/windows/win32/direct3d11/overviews-direct3d-11-render-multi-thread-command-list-play>)

# How to: Play Back a Command List

A [command list](./overviews-direct3d-11-render-multi-thread-command-list-e1b0cabde9.md) is a recorded list of rendering commands. Use a command list to pre-record drawing commands and play them back later. This topic shows how to play back a [command list](./overviews-direct3d-11-render-multi-thread-command-list-e1b0cabde9.md). A command list can be used to split rendering tasks between threads.

This section describes how to play back a command list. For recording a command list, see [How to: Record a Command List](./overviews-direct3d-11-render-multi-thread-command-list-record-432be84b16.md).

**To play back a command list**

-   Call [**ID3D11DeviceContext::ExecuteCommandList**](./nf-d3d11-id3d11devicecontext-executecommandlist-9a13a31f2f.md) and pass a valid [**ID3D11CommandList**](./nn-d3d11-id3d11commandlist-2848a61bff.md) object.
    ```
    if(g_pd3dCommandList)
    {
        g_pImmediateContext->ExecuteCommandList(g_pd3dCommandList, TRUE);
    }
    ```

    

[**ExecuteCommandList**](./nf-d3d11-id3d11devicecontext-executecommandlist-9a13a31f2f.md) must be executed on the [immediate context](./overviews-direct3d-11-devices-intro-469d7832b7.md) for recorded commands to be run on the graphics processing unit (GPU). Use the immediate context to feed commands to the GPU for execution, use a deferred context to record commands for playback onto another command list. When you call **ExecuteCommandList** onto another deferred context, you create a ‘merged’ deferred command list. To run the commands on the merged deferred command list, you need to execute them on the immediate context.

## Related topics

<dl> <dt>

[Command List](./overviews-direct3d-11-render-multi-thread-command-list-e1b0cabde9.md)
</dt> <dt>

[How to Use Direct3D 11](./how-to-use-direct3d-11-112ea0ccbf.md)
</dt> </dl>