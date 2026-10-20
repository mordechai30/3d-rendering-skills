Source: [https://learn.microsoft.com/en-us/windows/win32/api/d3d11_4/nf-d3d11_4-id3d11multithread-leave](<https://learn.microsoft.com/en-us/windows/win32/api/d3d11_4/nf-d3d11_4-id3d11multithread-leave>)

# ID3D11Multithread::Leave


## -description

Leave a device's critical section.



## -remarks

This function is typically used in multithreaded applications when there is a series of graphics commands 
		  that must happen in order. <a href="/windows/desktop/api/d3d11_4/nf-d3d11_4-id3d11multithread-enter">Enter</a> is typically called at the beginning of a series of graphics commands, and this function is typically 
		  called after those graphics commands.

## -see-also

<a href="/windows/desktop/api/d3d11_4/nn-d3d11_4-id3d11multithread">ID3D11Multithread</a>