Source: [https://learn.microsoft.com/en-us/windows/win32/api/D3D11/nf-d3d11-id3d11resource-getevictionpriority](<https://learn.microsoft.com/en-us/windows/win32/api/D3D11/nf-d3d11-id3d11resource-getevictionpriority>)

# ID3D11Resource::GetEvictionPriority


## -description

Get the eviction priority of a resource.



## -returns

Type: <b><a href="/windows/desktop/WinProg/windows-data-types">UINT</a></b>

One of the following values, which specifies the eviction priority for the resource:

<ul>
<li>DXGI_RESOURCE_PRIORITY_MINIMUM</li>
<li>DXGI_RESOURCE_PRIORITY_LOW</li>
<li>DXGI_RESOURCE_PRIORITY_NORMAL</li>
<li>DXGI_RESOURCE_PRIORITY_HIGH</li>
<li>DXGI_RESOURCE_PRIORITY_MAXIMUM</li>
</ul>

## -see-also

<a href="/windows/desktop/api/d3d11/nn-d3d11-id3d11resource">ID3D11Resource</a>