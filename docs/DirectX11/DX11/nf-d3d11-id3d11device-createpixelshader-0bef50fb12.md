Source: [https://learn.microsoft.com/en-us/windows/win32/api/D3D11/nf-d3d11-id3d11device-createpixelshader](<https://learn.microsoft.com/en-us/windows/win32/api/D3D11/nf-d3d11-id3d11device-createpixelshader>)

# ID3D11Device::CreatePixelShader


## -description

Create a pixel shader.

## -parameters

### -param pShaderBytecode [in]

Type: <b>const void*</b>

A pointer to the compiled shader.

### -param BytecodeLength [in]

Type: <b><a href="/windows/desktop/WinProg/windows-data-types">SIZE_T</a></b>

Size of the compiled pixel shader.

### -param pClassLinkage [in, optional]

Type: <b><a href="/windows/desktop/api/d3d11/nn-d3d11-id3d11classlinkage">ID3D11ClassLinkage</a>*</b>

A pointer to a class linkage interface (see <a href="/windows/desktop/api/d3d11/nn-d3d11-id3d11classlinkage">ID3D11ClassLinkage</a>); the value can be <b>NULL</b>.

### -param ppPixelShader [out, optional]

Type: <b><a href="/windows/desktop/api/d3d11/nn-d3d11-id3d11pixelshader">ID3D11PixelShader</a>**</b>

Address of a pointer to a <a href="/windows/desktop/api/d3d11/nn-d3d11-id3d11pixelshader">ID3D11PixelShader</a> interface. If this is <b>NULL</b>, all other parameters will be validated, and if all parameters pass validation this API will return S_FALSE instead of S_OK.

## -returns

Type: <b><a href="/windows/win32/com/structure-of-com-error-codes">HRESULT</a></b>

This method returns one of the following <a href="/windows/desktop/direct3d11/d3d11-graphics-reference-returnvalues">Direct3D 11 Return Codes</a>.

## -remarks

After creating the pixel shader, you can set it to the device using <a href="/windows/desktop/api/d3d11/nf-d3d11-id3d11devicecontext-pssetshader">ID3D11DeviceContext::PSSetShader</a>.

## -see-also

<a href="/windows/desktop/api/d3d11/nn-d3d11-id3d11device">ID3D11Device</a>