Source: [https://learn.microsoft.com/en-us/windows/win32/api/D3D11_1/nf-d3d11_1-id3duserdefinedannotation-getstatus](<https://learn.microsoft.com/en-us/windows/win32/api/D3D11_1/nf-d3d11_1-id3duserdefinedannotation-getstatus>)

# ID3DUserDefinedAnnotation::GetStatus


## -description

Determines whether the calling application is running under a Microsoft Direct3D profiling tool.



## -returns

The return value is nonzero if the calling application is running under a Direct3D profiling tool such as Visual Studio Ultimate 2012, and zero otherwise.

## -remarks

You can call <b>GetStatus</b> to determine whether your application is running under a Direct3D profiling tool before you make further calls to other methods of the <a href="/windows/desktop/api/d3d11_1/nn-d3d11_1-id3duserdefinedannotation">ID3DUserDefinedAnnotation</a> interface. For example, the <a href="/windows/desktop/api/d3d11_1/nf-d3d11_1-id3duserdefinedannotation-beginevent">ID3DUserDefinedAnnotation::BeginEvent</a> and <a href="/windows/desktop/api/d3d11_1/nf-d3d11_1-id3duserdefinedannotation-endevent">ID3DUserDefinedAnnotation::EndEvent</a> methods have no effect if the calling application is not running under an enabled Direct3D profiling tool. Therefore, you do not need to call these methods unless your application is running under a Direct3D profiling tool.


#### Examples

The following code shows how to use <b>GetStatus</b>.
          


```

#ifdef DEVELOPMENT_BUILD
    if ( pPerf->GetStatus() )
        m_MakeD3DAnnotationCalls = true;
#endif

…

   if ( m_ MakeD3DAnnotationCalls )
        pPerf->BeginEvent(L“Drawing Ocean”);
   MyDrawOceanRoutine();

          
```


<div class="code"></div>

## -see-also

<a href="/windows/desktop/api/d3d11_1/nn-d3d11_1-id3duserdefinedannotation">ID3DUserDefinedAnnotation</a>