Source: [https://learn.microsoft.com/en-us/windows/win32/api/D3D11_1/nf-d3d11_1-id3duserdefinedannotation-endevent](<https://learn.microsoft.com/en-us/windows/win32/api/D3D11_1/nf-d3d11_1-id3duserdefinedannotation-endevent>)

# ID3DUserDefinedAnnotation::EndEvent


## -description

Marks the end of a section of event code.



## -returns

Returns the number of previous calls to the <a href="/windows/desktop/api/d3d11_1/nf-d3d11_1-id3duserdefinedannotation-beginevent">ID3DUserDefinedAnnotation::BeginEvent</a> method that have not yet been finalized by calls to <b>EndEvent</b>.

The return value is –1 if the calling application is not running under a Direct3D profiling tool.

## -remarks

You call the <a href="/windows/desktop/api/d3d11_1/nf-d3d11_1-id3duserdefinedannotation-beginevent">BeginEvent</a> method to mark the beginning of the section of event code.

A user can visualize the event when the calling application is running under an enabled Direct3D profiling tool such as Microsoft Visual Studio Ultimate 2012.

<b>EndEvent</b> has no effect if the calling application is not running under an enabled Direct3D profiling tool.

## -see-also

<a href="/windows/desktop/api/d3d11_1/nn-d3d11_1-id3duserdefinedannotation">ID3DUserDefinedAnnotation</a>