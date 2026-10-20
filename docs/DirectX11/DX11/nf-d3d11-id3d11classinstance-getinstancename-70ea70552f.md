Source: [https://learn.microsoft.com/en-us/windows/win32/api/d3d11/nf-d3d11-id3d11classinstance-getinstancename](<https://learn.microsoft.com/en-us/windows/win32/api/d3d11/nf-d3d11-id3d11classinstance-getinstancename>)

# ID3D11ClassInstance::GetInstanceName


## -description

Gets the instance name of the current HLSL class.

## -parameters

### -param pInstanceName [out, optional]

Type: <b><a href="/windows/desktop/WinProg/windows-data-types">LPSTR</a></b>

The instance name of the current HLSL class.

### -param pBufferLength [in, out]

Type: <b><a href="/windows/desktop/WinProg/windows-data-types">SIZE_T</a>*</b>

The length of the <i>pInstanceName</i> parameter.

## -remarks

GetInstanceName will return a valid name only for instances acquired using 
          <a href="/windows/desktop/api/d3d11/nf-d3d11-id3d11classlinkage-getclassinstance">ID3D11ClassLinkage::GetClassInstance</a>.
        

For more information about using the <a href="/windows/desktop/api/d3d11/nn-d3d11-id3d11classinstance">ID3D11ClassInstance</a> interface, see 
          <a href="/windows/desktop/direct3dhlsl/overviews-direct3d-11-hlsl-dynamic-linking">Dynamic Linking</a>.
        

<b>Windows Phone 8:
        </b> This API is supported.

## -see-also

<a href="/windows/desktop/api/d3d11/nn-d3d11-id3d11classinstance">ID3D11ClassInstance</a>