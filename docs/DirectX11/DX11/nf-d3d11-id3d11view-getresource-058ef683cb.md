Source: [https://learn.microsoft.com/en-us/windows/win32/api/D3D11/nf-d3d11-id3d11view-getresource](<https://learn.microsoft.com/en-us/windows/win32/api/D3D11/nf-d3d11-id3d11view-getresource>)

# ID3D11View::GetResource


## -description

Get the resource that is accessed through this view.

## -parameters

### -param ppResource [out]

Type: <b><a href="/windows/desktop/api/d3d11/nn-d3d11-id3d11resource">ID3D11Resource</a>**</b>

Address of a pointer to the resource that is accessed through this view. (See <a href="/windows/desktop/api/d3d11/nn-d3d11-id3d11resource">ID3D11Resource</a>.)

## -remarks

This function increments the reference count of the resource by one, so it is necessary to call <b>Release</b> on the returned pointer when the application is done with it. Destroying (or losing) the returned pointer before <b>Release</b> is called will result in a memory leak.

## -see-also

<a href="/windows/desktop/api/d3d11/nn-d3d11-id3d11view">ID3D11View</a>