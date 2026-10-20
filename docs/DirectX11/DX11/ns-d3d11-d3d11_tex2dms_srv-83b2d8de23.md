Source: [https://learn.microsoft.com/en-us/windows/win32/api/D3D11/ns-d3d11-d3d11_tex2dms_srv](<https://learn.microsoft.com/en-us/windows/win32/api/D3D11/ns-d3d11-d3d11_tex2dms_srv>)

# D3D11_TEX2DMS_SRV structure


## -description

Specifies the subresources from a multisampled 2D texture to use in a shader-resource view.

## -struct-fields

### -field UnusedField_NothingToDefine

Type: <b><a href="/windows/desktop/WinProg/windows-data-types">UINT</a></b>

Integer of any value. See remarks.

## -remarks

Since a multisampled 2D texture contains a single subresource, there is actually nothing to specify in D3D11_TEX2DMS_RTV. Consequently, <b>UnusedField_NothingToDefine</b> is included so that this structure will compile in C.

## -see-also

<a href="/windows/desktop/direct3d11/d3d11-graphics-reference-resource-structures">Resource Structures</a>