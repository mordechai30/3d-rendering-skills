Source: [https://learn.microsoft.com/en-us/windows/win32/api/D3D11_1/nf-d3d11_1-id3duserdefinedannotation-beginevent](<https://learn.microsoft.com/en-us/windows/win32/api/D3D11_1/nf-d3d11_1-id3duserdefinedannotation-beginevent>)

# ID3DUserDefinedAnnotation::BeginEvent


## -description

Marks the beginning of a section of event code.

## -parameters

### -param Name [in]

A <b>NULL</b>-terminated <b>UNICODE</b> string that contains the name of the event. The name is not relevant to the operating system. You can choose a name that is meaningful when the calling application is running under the Direct3D profiling tool.
A <b>NULL</b> pointer produces undefined results.

## -returns

Returns the number of previous calls to <b>BeginEvent</b> that have not yet been finalized by calls to the <a href="/windows/desktop/api/d3d11_1/nf-d3d11_1-id3duserdefinedannotation-endevent">ID3DUserDefinedAnnotation::EndEvent</a> method.

The return value is –1 if the calling application is not running under a Direct3D profiling tool.

## -remarks

You call the <a href="/windows/desktop/api/d3d11_1/nf-d3d11_1-id3duserdefinedannotation-endevent">EndEvent</a> method to mark the end of the section of event code.

A user can visualize the event when the calling application is running under an enabled Direct3D profiling tool such as Microsoft Visual Studio Ultimate 2012.

<b>BeginEvent</b> has no effect if the calling application is not running under an enabled Direct3D profiling tool.


#### Examples

The following code shows how to use a pair of calls to the <b>BeginEvent</b> and <a href="/windows/desktop/api/d3d11_1/nf-d3d11_1-id3duserdefinedannotation-endevent">EndEvent</a> methods.
          It also uses the <a href="/previous-versions/visualstudio/visual-studio-2010/ezzw7k98(v=vs.100)">CComPtr</a> smart pointer type.


```cpp

CComPtr< ID3D11DeviceContext > pContext;

HRESULT hrCreateDevice = (*pfnD3D11CreateDevice)( 
        0,
        D3D_DRIVER_TYPE_NULL,
        0,
        0,
        NULL,
        0,
        D3D11_SDK_VERSION,
        NULL,
        0,
        & pContext );
VERIFY_SUCCEEDED(hrCreateDevice);
CComPtr<ID3DUserDefinedAnnotation> pPerf;
HRESULT hr = pContext->QueryInterface( __uuidof(pPerf), reinterpret_cast<void**>(&pPerf) );
if ( FAILED( hr ) ) 
    return;
pPerf->BeginEvent( L”Now entering ocean rendering code” );
MyDrawOceanRoutine( );
pPerf->EndEvent( );
          
```


<div class="code"></div>

## -see-also

<a href="/windows/desktop/api/d3d11_1/nn-d3d11_1-id3duserdefinedannotation">ID3DUserDefinedAnnotation</a>