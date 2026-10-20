Source: [https://learn.microsoft.com/en-us/windows/win32/api/D3D11/nf-d3d11-id3d11device-createclasslinkage](<https://learn.microsoft.com/en-us/windows/win32/api/D3D11/nf-d3d11-id3d11device-createclasslinkage>)

# ID3D11Device::CreateClassLinkage


## -description

Creates class linkage libraries to enable dynamic shader linkage.

## -parameters

### -param ppLinkage [out]

Type: <b><a href="/windows/desktop/api/d3d11/nn-d3d11-id3d11classlinkage">ID3D11ClassLinkage</a>**</b>

A pointer to a class-linkage interface pointer (see <a href="/windows/desktop/api/d3d11/nn-d3d11-id3d11classlinkage">ID3D11ClassLinkage</a>).

## -returns

Type: <b><a href="/windows/win32/com/structure-of-com-error-codes">HRESULT</a></b>

This method returns one of the following <a href="/windows/desktop/direct3d11/d3d11-graphics-reference-returnvalues">Direct3D 11 Return Codes</a>.

## -remarks

The <a href="/windows/desktop/api/d3d11/nn-d3d11-id3d11classlinkage">ID3D11ClassLinkage</a> interface returned in <i>ppLinkage</i> is associated with a shader by passing it as a parameter to one of the <a href="/windows/desktop/api/d3d11/nn-d3d11-id3d11device">ID3D11Device</a> create shader methods such as <a href="/windows/desktop/api/d3d11/nf-d3d11-id3d11device-createpixelshader">ID3D11Device::CreatePixelShader</a>.


#### Examples

Using CreateClassLinkage
          


```

ID3D11ClassLinkage * g_pPSClassLinkage = NULL;            
pd3dDevice->CreateClassLinkage( &g_pPSClassLinkage ); 
          
```


<div class="code"></div>

## -see-also

<a href="/windows/desktop/api/d3d11/nn-d3d11-id3d11device">ID3D11Device</a>