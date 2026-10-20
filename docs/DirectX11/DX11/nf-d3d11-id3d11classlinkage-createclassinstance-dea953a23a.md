Source: [https://learn.microsoft.com/en-us/windows/win32/api/D3D11/nf-d3d11-id3d11classlinkage-createclassinstance](<https://learn.microsoft.com/en-us/windows/win32/api/D3D11/nf-d3d11-id3d11classlinkage-createclassinstance>)

# ID3D11ClassLinkage::CreateClassInstance


## -description

Initializes a class-instance object that represents an HLSL class instance.

## -parameters

### -param pClassTypeName [in]

Type: <b><a href="/windows/desktop/WinProg/windows-data-types">LPCSTR</a></b>

The type name of a class to initialize.

### -param ConstantBufferOffset [in]

Type: <b><a href="/windows/desktop/WinProg/windows-data-types">UINT</a></b>

Identifies the constant buffer that contains the class data.

### -param ConstantVectorOffset [in]

Type: <b><a href="/windows/desktop/WinProg/windows-data-types">UINT</a></b>

The four-component vector offset from the start of the constant buffer where the class data will begin. Consequently, this is not a byte offset.

### -param TextureOffset [in]

Type: <b><a href="/windows/desktop/WinProg/windows-data-types">UINT</a></b>

The texture slot for the first texture; there may be multiple textures following the offset.

### -param SamplerOffset [in]

Type: <b><a href="/windows/desktop/WinProg/windows-data-types">UINT</a></b>

The sampler slot for the first sampler; there may be multiple samplers following the offset.

### -param ppInstance [out]

Type: <b><a href="/windows/desktop/api/d3d11/nn-d3d11-id3d11classinstance">ID3D11ClassInstance</a>**</b>

The address of a pointer to an <a href="/windows/desktop/api/d3d11/nn-d3d11-id3d11classinstance">ID3D11ClassInstance</a> interface to initialize.

## -returns

Type: <b><a href="/windows/win32/com/structure-of-com-error-codes">HRESULT</a></b>

Returns S_OK if successful; otherwise, returns one of the following <a href="/windows/desktop/direct3d11/d3d11-graphics-reference-returnvalues">Direct3D 11 Return Codes</a>.

## -remarks

Instances can be created (or gotten) before or after a shader is created. Use the same shader linkage object to acquire a class instance and create the shader the instance is going to be used in.

For more information about using the <a href="/windows/desktop/api/d3d11/nn-d3d11-id3d11classlinkage">ID3D11ClassLinkage</a> interface, see <a href="/windows/desktop/direct3dhlsl/overviews-direct3d-11-hlsl-dynamic-linking">Dynamic Linking</a>.
        

<b>Windows Phone 8:
        </b> This API is supported.

## -see-also

<a href="/windows/desktop/api/d3d11/nn-d3d11-id3d11classlinkage">ID3D11ClassLinkage</a>