Source: [https://learn.microsoft.com/en-us/windows/win32/api/D3D11/nf-d3d11-id3d11devicecontext-setresourceminlod](<https://learn.microsoft.com/en-us/windows/win32/api/D3D11/nf-d3d11-id3d11devicecontext-setresourceminlod>)

# ID3D11DeviceContext::SetResourceMinLOD


## -description

Sets the minimum level-of-detail (LOD) for a resource.

## -parameters

### -param pResource [in]

Type: <b><a href="/windows/desktop/api/d3d11/nn-d3d11-id3d11resource">ID3D11Resource</a>*</b>

A pointer to an <a href="/windows/desktop/api/d3d11/nn-d3d11-id3d11resource">ID3D11Resource</a> that represents the resource.

### -param MinLOD

Type: <b>FLOAT</b>

The level-of-detail, which ranges between 0 and the maximum number of mipmap levels of the resource. For example, the maximum number of mipmap levels of a 1D texture is specified in the  <b>MipLevels</b> member of the  <a href="/windows/desktop/api/d3d11/ns-d3d11-d3d11_texture1d_desc">D3D11_TEXTURE1D_DESC</a> structure.

## -remarks

To use a resource with <b>SetResourceMinLOD</b>, you must set the <a href="/windows/desktop/api/d3d11/ne-d3d11-d3d11_resource_misc_flag">D3D11_RESOURCE_MISC_RESOURCE_CLAMP</a> flag when you create that resource.

For Direct3D 10 and Direct3D 10.1, when sampling from a texture resource in a shader, the sampler can define a minimum LOD clamp to force sampling from less detailed mip levels.  For Direct3D 11, this functionality is extended from the sampler to the entire resource. Therefore, the application can specify the highest-resolution mip level of a resource that is available for access. This restricts the set of mip levels that are required to be resident in GPU memory, thereby saving memory.

The set of mip levels resident per-resource in GPU memory can be specified by the user.

Minimum LOD affects all of the resident mip levels. Therefore, only the resident mip levels can be updated and read from.

All methods that access texture resources must adhere to minimum LOD clamps.

Empty-set accesses are handled as out-of-bounds cases.

## -see-also

<a href="/windows/desktop/api/d3d11/nn-d3d11-id3d11devicecontext">ID3D11DeviceContext</a>