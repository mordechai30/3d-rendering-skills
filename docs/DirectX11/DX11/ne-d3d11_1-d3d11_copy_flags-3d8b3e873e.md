Source: [https://learn.microsoft.com/en-us/windows/win32/api/D3D11_1/ne-d3d11_1-d3d11_copy_flags](<https://learn.microsoft.com/en-us/windows/win32/api/D3D11_1/ne-d3d11_1-d3d11_copy_flags>)

# D3D11_COPY_FLAGS enumeration


## -description

<div class="alert"><b>Note</b>  This enumeration is supported by the Direct3D 11.1 runtime, which is available on Windows 8 and later operating systems.</div><div> </div>Specifies how to handle the existing contents of a resource during a copy or update operation of a region within that resource.

## -enum-fields

### -field D3D11_COPY_NO_OVERWRITE:0x1

The existing contents of the resource cannot be overwritten.

### -field D3D11_COPY_DISCARD:0x2

The existing contents of the resource are undefined and can be discarded.

## -see-also

<a href="/windows/desktop/direct3d11/d3d11-graphics-reference-d3d11-core-enums">Core Enumerations</a>



<a href="/windows/desktop/api/d3d11_1/nf-d3d11_1-id3d11devicecontext1-copysubresourceregion1">ID3D11DeviceContext1::CopySubresourceRegion1</a>



<a href="/windows/desktop/api/d3d11_1/nf-d3d11_1-id3d11devicecontext1-updatesubresource1">ID3D11DeviceContext1::UpdateSubresource1</a>