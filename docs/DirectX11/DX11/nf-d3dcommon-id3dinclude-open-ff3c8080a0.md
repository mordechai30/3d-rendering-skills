Source: [https://learn.microsoft.com/en-us/windows/win32/api/d3dcommon/nf-d3dcommon-id3dinclude-open](<https://learn.microsoft.com/en-us/windows/win32/api/d3dcommon/nf-d3dcommon-id3dinclude-open>)

# ID3DInclude::Open


## -description

A user-implemented method for opening and reading the contents of a shader #include file.

## -parameters

### -param IncludeType

Type: <b><a href="/windows/desktop/api/d3dcommon/ne-d3dcommon-d3d_include_type">D3D_INCLUDE_TYPE</a></b>

A <a href="/windows/desktop/api/d3dcommon/ne-d3dcommon-d3d_include_type">D3D_INCLUDE_TYPE</a>-typed value that indicates the location of the #include file.

### -param pFileName

Type: <b><a href="/windows/desktop/WinProg/windows-data-types">LPCSTR</a></b>

Name of the #include file.

### -param pParentData

Type: <b><a href="/windows/desktop/WinProg/windows-data-types">LPCVOID</a></b>

Pointer to the container that includes the #include file. The compiler might pass NULL in <i>pParentData</i>. For more information, see the "Searching for Include Files" section in <a href="/windows/desktop/direct3d11/d3d11-graphics-programming-guide-effects-compile">Compile an Effect (Direct3D 11)</a>.

### -param ppData

Type: <b><a href="/windows/desktop/WinProg/windows-data-types">LPCVOID</a>*</b>

Pointer to the buffer  that contains the include directives. This pointer remains valid until you call<a href="/windows/desktop/api/d3dcommon/nf-d3dcommon-id3dinclude-close">ID3DInclude::Close</a>.

### -param pBytes

Type: <b><a href="/windows/desktop/WinProg/windows-data-types">UINT</a>*</b>

Pointer to the number of bytes that <b>Open</b> returns in <i>ppData</i>.

## -returns

Type: <b><a href="/windows/win32/com/structure-of-com-error-codes">HRESULT</a></b>

The user-implemented method must return S_OK. If <b>Open</b> fails when it reads the #include file, the application programming interface (API) that caused <b>Open</b> to be called fails. This failure can occur in one of the following situations:
              

<ul>
<li>The high-level shader language (HLSL) shader fails one of the <b>D3D10CompileShader***</b> functions.
              </li>
<li>The effect fails one of the <b>D3D10CreateEffect***</b> functions.
              </li>
</ul>

## -see-also

<a href="/windows/desktop/api/d3dcommon/nn-d3dcommon-id3dinclude">ID3DInclude</a>



<a href="/windows/desktop/api/d3dcommon/nf-d3dcommon-id3dinclude-close">ID3DInclude::Close</a>