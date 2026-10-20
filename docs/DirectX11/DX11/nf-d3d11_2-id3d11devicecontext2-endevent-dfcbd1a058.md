Source: [https://learn.microsoft.com/en-us/windows/win32/api/d3d11_2/nf-d3d11_2-id3d11devicecontext2-endevent](<https://learn.microsoft.com/en-us/windows/win32/api/d3d11_2/nf-d3d11_2-id3d11devicecontext2-endevent>)

# ID3D11DeviceContext2::EndEvent


## -description

Allows applications to annotate the end of a range of graphics commands.



## -remarks

<b>EndEvent</b> allows applications to annotate the end of a range of graphics commands, in order to provide more context to what the GPU is executing. When the appropriate <a href="/previous-versions/dotnet/netframework-3.0/ms751538(v=vs.85)">ETW</a> logging is not enabled, this method does nothing. When ETW logging is enabled, an additional marker is correlated between the CPU and GPU timelines.

## -see-also

<a href="/windows/desktop/api/d3d11_2/nn-d3d11_2-id3d11devicecontext2">ID3D11DeviceContext2</a>