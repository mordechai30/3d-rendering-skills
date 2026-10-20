Source: [https://learn.microsoft.com/en-us/windows/win32/api/D3D11/nf-d3d11-id3d11devicecontext-dispatch](<https://learn.microsoft.com/en-us/windows/win32/api/D3D11/nf-d3d11-id3d11devicecontext-dispatch>)

# ID3D11DeviceContext::Dispatch


## -description

Execute a command list from a thread group.

## -parameters

### -param ThreadGroupCountX [in]

Type: <b><a href="/windows/desktop/WinProg/windows-data-types">UINT</a></b>

The number of groups dispatched in the x direction. <i>ThreadGroupCountX</i> must be less than or equal to D3D11_CS_DISPATCH_MAX_THREAD_GROUPS_PER_DIMENSION (65535).

### -param ThreadGroupCountY [in]

Type: <b><a href="/windows/desktop/WinProg/windows-data-types">UINT</a></b>

The number of groups dispatched in the y direction. <i>ThreadGroupCountY</i> must be less than or equal to D3D11_CS_DISPATCH_MAX_THREAD_GROUPS_PER_DIMENSION (65535).

### -param ThreadGroupCountZ [in]

Type: <b><a href="/windows/desktop/WinProg/windows-data-types">UINT</a></b>

The number of groups dispatched in the z direction.  <i>ThreadGroupCountZ</i> must be less than or equal to D3D11_CS_DISPATCH_MAX_THREAD_GROUPS_PER_DIMENSION (65535). 
        In feature level 10 the value for <i>ThreadGroupCountZ</i> must be 1.

## -remarks

You call the <b>Dispatch</b> method to execute commands in a <a href="/windows/desktop/direct3d11/direct3d-11-advanced-stages-compute-shader">compute shader</a>. A compute shader can be run on many threads in parallel, within a thread group. Index a particular thread, within a thread group using a 3D vector 
      given by (x,y,z).

In the following illustration, assume a thread group with 50 threads where the size of the group is given by (5,5,2). A single thread is identified from a 
      thread group with 50 threads in it, using the vector (4,1,1).

<img alt="Illustration of a single thread within a thread group of 50 threads" src="./images/d3d11_thread_group_1.png"/>

The following illustration shows the relationship between the parameters passed to <b>ID3D11DeviceContext::Dispatch</b>, Dispatch(5,3,2), the values specified in the <a href="/windows/desktop/direct3dhlsl/sm5-attributes-numthreads">numthreads</a> attribute, numthreads(10,8,3), and values that will passed to the compute shader for the thread-related system values 
(<a href="/previous-versions/windows/desktop/legacy/ff471569(v=vs.85)">SV_GroupIndex</a>,<a href="/windows/desktop/direct3dhlsl/sv-dispatchthreadid">SV_DispatchThreadID</a>,<a href="/windows/desktop/direct3dhlsl/sv-groupthreadid">SV_GroupThreadID</a>,<a href="/windows/desktop/direct3dhlsl/sv-groupid">SV_GroupID</a>).

<img alt="Illustration of the relationship between Dispatch, thread groups, and threads" src="./images/ThreadGroupIDs.png"/>

## -see-also

<a href="/windows/desktop/api/d3d11/nn-d3d11-id3d11devicecontext">ID3D11DeviceContext</a>