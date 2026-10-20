Source: [https://learn.microsoft.com/en-us/windows/win32/api/D3D11/nf-d3d11-id3d11devicecontext-executecommandlist](<https://learn.microsoft.com/en-us/windows/win32/api/D3D11/nf-d3d11-id3d11devicecontext-executecommandlist>)

# ID3D11DeviceContext::ExecuteCommandList


## -description

Queues commands from a command list onto a device.

## -parameters

### -param pCommandList [in]

Type: <b><a href="/windows/desktop/api/d3d11/nn-d3d11-id3d11commandlist">ID3D11CommandList</a>*</b>

A pointer to an <a href="/windows/desktop/api/d3d11/nn-d3d11-id3d11commandlist">ID3D11CommandList</a> interface that encapsulates a command list.

### -param RestoreContextState

Type: <b><a href="/windows/desktop/WinProg/windows-data-types">BOOL</a></b>

A Boolean flag that determines whether the target context state is saved prior to and restored after the execution of a command list. Use <b>TRUE</b> to indicate that the runtime needs to save and restore the state. Use <b>FALSE</b> to indicate that no state shall be saved or restored, which causes the target context to  return to its default state after the command list executes. Applications should typically use <b>FALSE</b> unless they will restore the state to be nearly equivalent to the state that the runtime would restore if <b>TRUE</b> were passed. When applications use <b>FALSE</b>, they can avoid unnecessary and inefficient state transitions.

## -remarks

Use this method to play back a command list that was recorded by a deferred context on any thread.

A call to <b>ExecuteCommandList</b> of a command list from a deferred context onto the immediate context is required for the recorded commands to be executed on the graphics processing unit (GPU). A call to <b>ExecuteCommandList</b> of a command list from a deferred context onto another deferred context can be used to merge recorded lists. But to run the commands from the merged deferred command list on the GPU, you need to execute them on the immediate context.
        

This method performs some runtime validation related to queries. Queries that are begun in a device context cannot be manipulated indirectly by executing a command list (that is, Begin or End was invoked against the same query by the deferred context which generated the command list). If such a condition occurs, the ExecuteCommandList method does not execute the command list. However, the state of the device context is still maintained, as would be expected (<a href="/windows/desktop/api/d3d11/nf-d3d11-id3d11devicecontext-clearstate">ID3D11DeviceContext::ClearState</a> is performed, unless the application indicates to preserve the device context state).
        

<b>Windows Phone 8:
        </b> This API is supported.

## -see-also

<a href="/windows/desktop/api/d3d11/nn-d3d11-id3d11devicecontext">ID3D11DeviceContext</a>