Source: [https://learn.microsoft.com/en-us/windows/win32/api/d3d11_2/nf-d3d11_2-id3d11devicecontext2-isannotationenabled](<https://learn.microsoft.com/en-us/windows/win32/api/d3d11_2/nf-d3d11_2-id3d11devicecontext2-isannotationenabled>)

# ID3D11DeviceContext2::IsAnnotationEnabled


## -description

Allows apps to determine when either a capture or profiling request is enabled.



## -returns

Returns <b>TRUE</b> if capture or profiling is enabled and <b>FALSE</b> otherwise.

## -remarks

Returns <b>TRUE</b> if the capture tool is present and capturing or the app is being profiled such that <a href="/windows/desktop/api/d3d11_2/nf-d3d11_2-id3d11devicecontext2-setmarkerint">SetMarkerInt</a> or <a href="/windows/desktop/api/d3d11_2/nf-d3d11_2-id3d11devicecontext2-begineventint">BeginEventInt</a> will be logged to <a href="/previous-versions/dotnet/netframework-3.0/ms751538(v=vs.85)">ETW</a>. Otherwise, it returns <b>FALSE</b>. Apps can use this to turn off self-throttling mechanisms in order to accurately capture what is currently being seen as app output. Apps can also avoid generating event markers and the associated overhead it may entail when there is no benefit to do so. 

If apps detect that capture is being performed, they can prevent the Direct3D debugging tools, such as Microsoft Visual Studio 2013, from capturing them. The purpose of the <a href="/windows/desktop/api/d3d11/ne-d3d11-d3d11_create_device_flag">D3D11_CREATE_DEVICE_PREVENT_ALTERING_LAYER_SETTINGS_FROM_REGISTRY</a> flag prior to Windows 8.1 was to allow the Direct3D runtime to prevent debugging tools from capturing apps.

## -see-also

<a href="/windows/desktop/api/d3d11_2/nn-d3d11_2-id3d11devicecontext2">ID3D11DeviceContext2</a>