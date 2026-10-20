Source: [https://learn.microsoft.com/en-us/windows/win32/api/D3D11Shader/nf-d3d11shader-id3d11moduleinstance-bindconstantbuffer](<https://learn.microsoft.com/en-us/windows/win32/api/D3D11Shader/nf-d3d11shader-id3d11moduleinstance-bindconstantbuffer>)

# ID3D11ModuleInstance::BindConstantBuffer


## -description

Rebinds a constant buffer from a source slot to a destination slot.

## -parameters

### -param uSrcSlot [in]

Type: <b><a href="/windows/desktop/WinProg/windows-data-types">UINT</a></b>

The source slot number for rebinding.

### -param uDstSlot [in]

Type: <b><a href="/windows/desktop/WinProg/windows-data-types">UINT</a></b>

The destination slot number for rebinding.

### -param cbDstOffset [in]

Type: <b><a href="/windows/desktop/WinProg/windows-data-types">UINT</a></b>

The offset in bytes of the destination slot for rebinding. The offset must have 16-byte alignment.

## -returns

Type: <b><a href="/windows/win32/com/structure-of-com-error-codes">HRESULT</a></b>

Returns:

<ul>
<li><b>S_OK</b> for a valid rebinding
              </li>
<li><b>S_FALSE</b> for rebinding a nonexistent slot; that is, for which the shader reflection doesn’t have any data
              </li>
<li><b>E_FAIL</b> for an invalid rebinding, for example, the rebinding is out-of-bounds
              </li>
<li>Possibly one of the other <a href="/windows/desktop/direct3d11/d3d11-graphics-reference-returnvalues">Direct3D 11 Return Codes</a>
</li>
</ul>

## -see-also

<a href="/windows/desktop/api/d3d11shader/nn-d3d11shader-id3d11moduleinstance">ID3D11ModuleInstance</a>