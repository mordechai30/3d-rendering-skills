Source: [https://learn.microsoft.com/en-us/windows/win32/api/D3D11Shader/ns-d3d11shader-d3d11_library_desc](<https://learn.microsoft.com/en-us/windows/win32/api/D3D11Shader/ns-d3d11shader-d3d11_library_desc>)

# D3D11_LIBRARY_DESC structure


## -description

Describes a library.

## -struct-fields

### -field Creator

Type: <b><a href="/windows/desktop/WinProg/windows-data-types">LPCSTR</a></b>

The name of the originator of the library.

### -field Flags

Type: <b><a href="/windows/desktop/WinProg/windows-data-types">UINT</a></b>

A combination of <a href="/windows/desktop/direct3dhlsl/d3dcompile-constants">D3DCOMPILE Constants</a> that are combined by using a bitwise OR operation. The resulting value specifies how the compiler compiles.

### -field FunctionCount

Type: <b><a href="/windows/desktop/WinProg/windows-data-types">UINT</a></b>

The number of functions exported from the library.

## -see-also

<a href="/windows/desktop/api/d3d11shader/nf-d3d11shader-id3d11libraryreflection-getdesc">ID3D11LibraryReflection::GetDesc</a>



<a href="/windows/desktop/direct3d11/d3d11-graphics-reference-shader-structures">Shader Structures</a>