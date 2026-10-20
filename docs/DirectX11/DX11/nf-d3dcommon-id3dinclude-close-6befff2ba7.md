Source: [https://learn.microsoft.com/en-us/windows/win32/api/d3dcommon/nf-d3dcommon-id3dinclude-close](<https://learn.microsoft.com/en-us/windows/win32/api/d3dcommon/nf-d3dcommon-id3dinclude-close>)

# ID3DInclude::Close


## -description

A user-implemented method for closing a shader #include file.

## -parameters

### -param pData

Type: <b><a href="/windows/desktop/WinProg/windows-data-types">LPCVOID</a></b>

Pointer to the buffer that contains the include directives. This is the pointer that was returned by the corresponding <a href="/windows/desktop/api/d3dcommon/nf-d3dcommon-id3dinclude-open">ID3DInclude::Open</a> call.

## -returns

Type: <b><a href="/windows/win32/com/structure-of-com-error-codes">HRESULT</a></b>

The user-implemented <b>Close</b> method should return S_OK. If <b>Close</b> fails when it closes the #include file, the application programming interface (API) that caused <b>Close</b> to be called fails. This failure can occur in one of the following situations:
              

<ul>
<li>The high-level shader language (HLSL) shader fails one of the <b>D3D10CompileShader***</b> functions.
              </li>
<li>The effect fails one of the <b>D3D10CreateEffect***</b> functions.
              </li>
</ul>

## -remarks

If <a href="/windows/desktop/api/d3dcommon/nf-d3dcommon-id3dinclude-open">ID3DInclude::Open</a> was successful, <b>Close</b> is guaranteed to be called before the API using the <a href="/windows/desktop/api/d3dcommon/nn-d3dcommon-id3dinclude">ID3DInclude</a> interface returns.

## -see-also

<a href="/windows/desktop/api/d3dcommon/nn-d3dcommon-id3dinclude">ID3DInclude</a>



<a href="/windows/desktop/api/d3dcommon/nf-d3dcommon-id3dinclude-open">ID3DInclude::Open</a>