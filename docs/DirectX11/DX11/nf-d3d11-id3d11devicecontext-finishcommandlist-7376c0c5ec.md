Source: [https://learn.microsoft.com/en-us/windows/win32/api/D3D11/nf-d3d11-id3d11devicecontext-finishcommandlist](<https://learn.microsoft.com/en-us/windows/win32/api/D3D11/nf-d3d11-id3d11devicecontext-finishcommandlist>)

# ID3D11DeviceContext::FinishCommandList


## -description

Create a command list and record graphics commands into it.

## -parameters

### -param RestoreDeferredContextState

Type: <b><a href="/windows/desktop/WinProg/windows-data-types">BOOL</a></b>

A Boolean flag that determines whether the runtime saves deferred context state before it executes  <b>FinishCommandList</b> and restores it afterwards. Use <b>TRUE</b> to indicate that the runtime needs to save and restore the state. Use <b>FALSE</b> to indicate that the runtime will not save or restore any state. In this case, the deferred context will  return to its default state after the call to  <b>FinishCommandList</b> completes. For information about default state, see <a href="/windows/desktop/api/d3d11/nf-d3d11-id3d11devicecontext-clearstate">ID3D11DeviceContext::ClearState</a>. Typically, use <b>FALSE</b> unless you restore the state to be nearly equivalent to the state that the runtime would restore if you passed <b>TRUE</b>. When you use <b>FALSE</b>, you can avoid unnecessary and inefficient state transitions.
            

<div class="alert"><b>Note</b>  This parameter does not affect the command list that the current call to <b>FinishCommandList</b> returns. However, this parameter affects the command list of the next call to <b>FinishCommandList</b> on the same deferred context.
            </div>
<div> </div>

### -param ppCommandList [out, optional]

Type: <b><a href="/windows/desktop/api/d3d11/nn-d3d11-id3d11commandlist">ID3D11CommandList</a>**</b>

Upon completion of the method, the passed pointer to an <a href="/windows/desktop/api/d3d11/nn-d3d11-id3d11commandlist">ID3D11CommandList</a> interface pointer is initialized with the recorded command list information. The resulting <b>ID3D11CommandList</b> object is immutable and can only be used with <a href="/windows/desktop/api/d3d11/nf-d3d11-id3d11devicecontext-executecommandlist">ID3D11DeviceContext::ExecuteCommandList</a>.

## -returns

Type: <b><a href="/windows/win32/com/structure-of-com-error-codes">HRESULT</a></b>

Returns S_OK if successful; otherwise, returns one of the following:

<ul>
<li>Returns DXGI_ERROR_DEVICE_REMOVED if the video card has been physically removed from the system, or a driver upgrade for the video card has occurred. If this error occurs, you should destroy and recreate the device.</li>
<li>Returns DXGI_ERROR_INVALID_CALL if <b>FinishCommandList</b> cannot be called from the current context. See remarks.
              </li>
<li>Returns E_OUTOFMEMORY if the application has exhausted available memory.</li>
</ul>

## -remarks

Create a command list from a deferred context and record commands into it by calling <b>FinishCommandList</b>. Play back a command list with an immediate context by calling <a href="/windows/desktop/api/d3d11/nf-d3d11-id3d11devicecontext-executecommandlist">ID3D11DeviceContext::ExecuteCommandList</a>.
        

Immediate context state is cleared before and after a command list is executed. A command list has no concept of inheritance. Each call to <b>FinishCommandList</b> will record only the state set since any previous call to  <b>FinishCommandList</b>.
        

For example, the state of a <a href="/windows/desktop/direct3d11/overviews-direct3d-11-devices-intro">device context</a> is its render state or pipeline state. To retrieve device context state, an application can call  <a href="/windows/desktop/api/d3d11/nf-d3d11-id3d11devicecontext-getdata">ID3D11DeviceContext::GetData</a> or  <a href="/windows/desktop/api/d3d11/nf-d3d11-id3d11devicecontext-getpredication">ID3D11DeviceContext::GetPredication</a>.
        

For more information about how to use <b>FinishCommandList</b>, see <a href="/windows/desktop/direct3d11/overviews-direct3d-11-render-multi-thread-command-list-record">How to: Record a Command List</a>.
        

<b>Windows Phone 8:
        </b> This API is supported.

## -see-also

<a href="/windows/desktop/api/d3d11/nn-d3d11-id3d11devicecontext">ID3D11DeviceContext</a>