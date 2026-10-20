Source: [https://learn.microsoft.com/en-us/windows/win32/api/d3d11_4/nf-d3d11_4-id3d11multithread-enter](<https://learn.microsoft.com/en-us/windows/win32/api/d3d11_4/nf-d3d11_4-id3d11multithread-enter>)

# ID3D11Multithread::Enter


## -description

Enter a device's critical section.



## -remarks

If <a href="/windows/desktop/api/d3d11_4/nf-d3d11_4-id3d11multithread-setmultithreadprotected">SetMultithreadProtected</a> is set to true, then entering a device's critical section prevents other threads from simultaneously calling that device's methods, calling DXGI methods, and calling the methods of all resource, view, shader, state, and asynchronous interfaces.

This function should be used in multithreaded applications when there is a series of graphics commands that must happen in order. This function is typically called at the beginning of the series of graphics commands, and <a href="/windows/desktop/api/d3d11_4/nf-d3d11_4-id3d11multithread-leave">Leave</a> is typically called after those graphics commands.

## -see-also

<a href="/windows/desktop/api/d3d11_4/nn-d3d11_4-id3d11multithread">ID3D11Multithread</a>