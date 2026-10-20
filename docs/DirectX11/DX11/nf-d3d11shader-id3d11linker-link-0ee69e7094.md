Source: [https://learn.microsoft.com/en-us/windows/win32/api/D3D11Shader/nf-d3d11shader-id3d11linker-link](<https://learn.microsoft.com/en-us/windows/win32/api/D3D11Shader/nf-d3d11shader-id3d11linker-link>)

# ID3D11Linker::Link


## -description

Links the shader and produces a shader blob that the Direct3D runtime can use.

## -parameters

### -param pEntry [in]

Type: <b><a href="/windows/desktop/api/d3d11shader/nn-d3d11shader-id3d11moduleinstance">ID3D11ModuleInstance</a>*</b>

A pointer to the <a href="/windows/desktop/api/d3d11shader/nn-d3d11shader-id3d11moduleinstance">ID3D11ModuleInstance</a> interface for the shader module instance to link from.

### -param pEntryName [in]

Type: <b><a href="/windows/desktop/WinProg/windows-data-types">LPCSTR</a></b>

The name of the shader module instance to link from.

### -param pTargetName [in]

Type: <b><a href="/windows/desktop/WinProg/windows-data-types">LPCSTR</a></b>

The name for the shader blob that is produced.

### -param uFlags [in]

Type: <b><a href="/windows/desktop/WinProg/windows-data-types">UINT</a></b>

Reserved.

### -param ppShaderBlob [out]

Type: <b><a href="/previous-versions/windows/desktop/legacy/ff728743(v=vs.85)">ID3DBlob</a>**</b>

A pointer to a variable that receives a pointer to the <a href="/previous-versions/windows/desktop/legacy/ff728743(v=vs.85)">ID3DBlob</a> interface that you can use to access the compiled shader code.

### -param ppErrorBuffer [out, optional]

Type: <b><a href="/previous-versions/windows/desktop/legacy/ff728743(v=vs.85)">ID3DBlob</a>**</b>

A pointer to a variable that receives a pointer to the <a href="/previous-versions/windows/desktop/legacy/ff728743(v=vs.85)">ID3DBlob</a> interface that you can use to access compiler error messages.

## -returns

Type: <b><a href="/windows/win32/com/structure-of-com-error-codes">HRESULT</a></b>

Returns S_OK if successful; otherwise, returns one of the <a href="/windows/desktop/direct3d11/d3d11-graphics-reference-returnvalues">Direct3D 11 Return Codes</a>.

## -see-also

<a href="/windows/desktop/api/d3d11shader/nn-d3d11shader-id3d11linker">ID3D11Linker</a>