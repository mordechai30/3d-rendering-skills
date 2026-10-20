Source: [https://learn.microsoft.com/en-us/windows/win32/api/D3D11Shader/nf-d3d11shader-id3d11moduleinstance-bindunorderedaccessviewbyname](<https://learn.microsoft.com/en-us/windows/win32/api/D3D11Shader/nf-d3d11shader-id3d11moduleinstance-bindunorderedaccessviewbyname>)

# ID3D11ModuleInstance::BindUnorderedAccessViewByName


## -description

Rebinds an unordered access view (UAV) by name to destination slots.

## -parameters

### -param pName [in]

Type: <b><a href="/windows/desktop/WinProg/windows-data-types">LPCSTR</a></b>

The name of the UAV for rebinding.

### -param uDstSlot [in]

Type: <b><a href="/windows/desktop/WinProg/windows-data-types">UINT</a></b>

The first destination slot number for rebinding.

### -param uCount [in]

Type: <b><a href="/windows/desktop/WinProg/windows-data-types">UINT</a></b>

The number of slots for rebinding.

## -returns

Type: <b><a href="/windows/win32/com/structure-of-com-error-codes">HRESULT</a></b>

Returns:

<ul>
<li><b>S_OK</b> for a valid rebinding</li>
<li><b>S_FALSE</b> for rebinding a nonexistent slot; that is, for which the shader reflection doesn’t have any data</li>
<li><b>E_FAIL</b> for an invalid rebinding, for example, the rebinding is out-of-bounds</li>
<li>Possibly one of the other <a href="/windows/desktop/direct3d11/d3d11-graphics-reference-returnvalues">Direct3D 11 Return Codes</a>
</li>
</ul>

## -see-also

<a href="/windows/desktop/api/d3d11shader/nn-d3d11shader-id3d11moduleinstance">ID3D11ModuleInstance</a>