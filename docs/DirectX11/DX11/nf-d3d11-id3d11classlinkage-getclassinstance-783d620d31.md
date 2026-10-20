Source: [https://learn.microsoft.com/en-us/windows/win32/api/D3D11/nf-d3d11-id3d11classlinkage-getclassinstance](<https://learn.microsoft.com/en-us/windows/win32/api/D3D11/nf-d3d11-id3d11classlinkage-getclassinstance>)

# ID3D11ClassLinkage::GetClassInstance


## -description

Gets the class-instance object that represents the specified HLSL class.

## -parameters

### -param pClassInstanceName [in]

Type: <b><a href="/windows/desktop/WinProg/windows-data-types">LPCSTR</a></b>

The name of a class for which to get the class instance.

### -param InstanceIndex [in]

Type: <b><a href="/windows/desktop/WinProg/windows-data-types">UINT</a></b>

The index of the class instance.

### -param ppInstance [out]

Type: <b><a href="/windows/desktop/api/d3d11/nn-d3d11-id3d11classinstance">ID3D11ClassInstance</a>**</b>

The address of a pointer to an <a href="/windows/desktop/api/d3d11/nn-d3d11-id3d11classinstance">ID3D11ClassInstance</a> interface to initialize.

## -returns

Type: <b><a href="/windows/win32/com/structure-of-com-error-codes">HRESULT</a></b>

Returns S_OK if successful; otherwise, returns one of the <a href="/windows/desktop/direct3d11/d3d11-graphics-reference-returnvalues">Direct3D 11 Return Codes</a>.

## -remarks

For more information about using the <a href="/windows/desktop/api/d3d11/nn-d3d11-id3d11classlinkage">ID3D11ClassLinkage</a> interface, see
          <a href="/windows/desktop/direct3dhlsl/overviews-direct3d-11-hlsl-dynamic-linking">Dynamic Linking</a>.
        

A class instance must have at least 1 data member in order to be available for the runtime to use with
          <b>ID3D11ClassLinkage::GetClassInstance</b>.
          Any instance with no members will be optimized out of a compiled shader blob as a zero-sized object.
          If you have a class with no data members, use
          <a href="/windows/desktop/api/d3d11/nf-d3d11-id3d11classlinkage-createclassinstance">ID3D11ClassLinkage::CreateClassInstance</a> instead.
        

<b>Windows Phone 8:
        </b> This API is supported.

## -see-also

<a href="/windows/desktop/api/d3d11/nn-d3d11-id3d11classinstance">ID3D11ClassInstance</a>



<a href="/windows/desktop/api/d3d11/nn-d3d11-id3d11classlinkage">ID3D11ClassLinkage</a>