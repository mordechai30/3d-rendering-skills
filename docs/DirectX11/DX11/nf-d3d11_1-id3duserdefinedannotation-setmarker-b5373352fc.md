Source: [https://learn.microsoft.com/en-us/windows/win32/api/D3D11_1/nf-d3d11_1-id3duserdefinedannotation-setmarker](<https://learn.microsoft.com/en-us/windows/win32/api/D3D11_1/nf-d3d11_1-id3duserdefinedannotation-setmarker>)

# ID3DUserDefinedAnnotation::SetMarker


## -description

Marks a single point of execution in code.

## -parameters

### -param Name [in]

A <b>NULL</b>-terminated <b>UNICODE</b> string that contains the name of the marker. The name is not relevant to the operating system. You can choose a name that is meaningful when the calling application is running under the Direct3D profiling tool.
A <b>NULL</b> pointer produces undefined results.

## -remarks

A user can visualize the marker when the calling application is running under an enabled Direct3D profiling tool such as Microsoft Visual Studio Ultimate 2012.

<b>SetMarker</b> has no effect if the calling application is not running under an enabled Direct3D profiling tool.


#### Examples

The following code shows how to use <b>SetMarker</b>.
          It also uses the <a href="/previous-versions/visualstudio/visual-studio-2010/ezzw7k98(v=vs.100)">CComPtr</a> smart pointer type.


```

CComPtr< ID3D11DeviceContext > pID3D11DeviceContext;

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
        & pID3D11DeviceContext );
VERIFY_SUCCEEDED(hrCreateDevice);

CComPtr<ID3DUserDefinedAnnotation> pPerf;
HRESULT hr = pID3D11DeviceContext->QueryInterface( __uuidof(pPerf), reinterpret_cast<void**>(&pPerf) );
if ( FAILED( hr ) ) 
    return;
pPerf->SetMarker( L”Occlusion test failed- not drawing sun flare” );

          
```


<div class="code"></div>

## -see-also

<a href="/windows/desktop/api/d3d11_1/nn-d3d11_1-id3duserdefinedannotation">ID3DUserDefinedAnnotation</a>