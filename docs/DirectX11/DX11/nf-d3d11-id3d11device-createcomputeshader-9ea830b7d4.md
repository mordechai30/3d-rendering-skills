Source: [https://learn.microsoft.com/en-us/windows/win32/api/D3D11/nf-d3d11-id3d11device-createcomputeshader](<https://learn.microsoft.com/en-us/windows/win32/api/D3D11/nf-d3d11-id3d11device-createcomputeshader>)

# ID3D11Device::CreateComputeShader


## -description

Create a <a href="/windows/desktop/direct3d11/direct3d-11-advanced-stages-compute-shader">compute shader</a>.

## -parameters

### -param pShaderBytecode [in]

Type: <b>const void*</b>

A pointer to a compiled shader.

### -param BytecodeLength [in]

Type: <b><a href="/windows/desktop/WinProg/windows-data-types">SIZE_T</a></b>

Size of the compiled shader in <i>pShaderBytecode</i>.

### -param pClassLinkage [in, optional]

Type: <b><a href="/windows/desktop/api/d3d11/nn-d3d11-id3d11classlinkage">ID3D11ClassLinkage</a>*</b>

A pointer to a <a href="/windows/desktop/api/d3d11/nn-d3d11-id3d11classlinkage">ID3D11ClassLinkage</a>, which represents  class linkage interface; the value can be <b>NULL</b>.

### -param ppComputeShader [out, optional]

Type: <b><a href="/windows/desktop/api/d3d11/nn-d3d11-id3d11computeshader">ID3D11ComputeShader</a>**</b>

Address of a pointer to an <a href="/windows/desktop/api/d3d11/nn-d3d11-id3d11computeshader">ID3D11ComputeShader</a> interface. If this is <b>NULL</b>, 
        all other parameters will be validated; if validation passes, CreateComputeShader returns S_FALSE instead of S_OK.

## -returns

Type: <b><a href="/windows/win32/com/structure-of-com-error-codes">HRESULT</a></b>

This method returns E_OUTOFMEMORY if there is insufficient memory to create the compute shader.  
        See <a href="/windows/desktop/direct3d11/d3d11-graphics-reference-returnvalues">Direct3D 11 Return Codes</a> for other possible return values.

## -remarks

For an example, see <a href="/windows/desktop/direct3d11/direct3d-11-advanced-stages-compute-create">How To: Create a Compute Shader</a> and <a href="https://msdn.microsoft.com/library/Ee416569(v=VS.85).aspx">HDRToneMappingCS11 Sample</a>.

## -see-also

<a href="/windows/desktop/api/d3d11/nn-d3d11-id3d11device">ID3D11Device</a>