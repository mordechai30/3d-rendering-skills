Source: [https://learn.microsoft.com/en-us/windows/win32/api/D3D11/nf-d3d11-id3d11devicecontext-omgetblendstate](<https://learn.microsoft.com/en-us/windows/win32/api/D3D11/nf-d3d11-id3d11devicecontext-omgetblendstate>)

# ID3D11DeviceContext::OMGetBlendState


## -description

Get the blend state of the output-merger stage.

## -parameters

### -param ppBlendState [out, optional]

Type: <b><a href="/windows/desktop/api/d3d11/nn-d3d11-id3d11blendstate">ID3D11BlendState</a>**</b>

Address of a pointer to a blend-state interface (see <a href="/windows/desktop/api/d3d11/nn-d3d11-id3d11blendstate">ID3D11BlendState</a>).

### -param BlendFactor [out, optional]

Type: <b><a href="/windows/desktop/WinProg/windows-data-types">FLOAT</a>[4]</b>

Array of blend factors, one for each RGBA component.

### -param pSampleMask [out, optional]

Type: <b><a href="/windows/desktop/WinProg/windows-data-types">UINT</a>*</b>

Pointer to a <a href="/windows/desktop/api/d3d11/nf-d3d11-id3d11devicecontext-omsetblendstate">sample mask</a>.

## -remarks

The reference count of the returned interface will be incremented by one when the blend state is retrieved. Applications must release returned pointer(s) when they are no longer needed, or else there will be a memory leak.

<b>Windows Phone 8:
        </b> This API is supported.

## -see-also

<a href="/windows/desktop/api/d3d11/nn-d3d11-id3d11devicecontext">ID3D11DeviceContext</a>