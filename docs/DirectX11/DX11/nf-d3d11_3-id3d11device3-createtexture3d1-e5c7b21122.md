Source: [https://learn.microsoft.com/en-us/windows/win32/api/D3D11_3/nf-d3d11_3-id3d11device3-createtexture3d1](<https://learn.microsoft.com/en-us/windows/win32/api/D3D11_3/nf-d3d11_3-id3d11device3-createtexture3d1>)

# ID3D11Device3::CreateTexture3D1


## -description

Creates a <a href="/windows/desktop/direct3d11/overviews-direct3d-11-resources-textures-intro">3D texture</a>.

## -parameters

### -param pDesc1 [in]

Type: <b>const <a href="/windows/desktop/api/d3d11_3/ns-d3d11_3-cd3d11_texture3d_desc1">D3D11_TEXTURE3D_DESC1</a>*</b>

A pointer to a <a href="/windows/desktop/api/d3d11_3/ns-d3d11_3-cd3d11_texture3d_desc1">D3D11_TEXTURE3D_DESC1</a> structure that describes a 3D texture resource. To create a typeless resource that can be interpreted at runtime into different, compatible formats, specify a typeless format in the texture description. To generate mipmap levels automatically, set the number of mipmap levels to 0.

### -param pInitialData [in, optional]

Type: <b>const <a href="/windows/desktop/api/d3d11/ns-d3d11-d3d11_subresource_data">D3D11_SUBRESOURCE_DATA</a>*</b>

A pointer to an array of <a href="/windows/desktop/api/d3d11/ns-d3d11-d3d11_subresource_data">D3D11_SUBRESOURCE_DATA</a> structures that describe subresources for the 3D texture resource. Applications can't specify <b>NULL</b> for <i>pInitialData</i> when creating IMMUTABLE resources (see <a href="/windows/desktop/api/d3d11/ne-d3d11-d3d11_usage">D3D11_USAGE</a>). If the resource is multisampled, <i>pInitialData</i> must be <b>NULL</b> because multisampled resources can't be initialized with data when they are created.

If you don't pass anything to <i>pInitialData</i>, the initial content of the memory for the resource is undefined. In this case, you need to write the resource content some other way before the resource is read.

You can determine the size of this array from the value in the <b>MipLevels</b> member of the <b>D3D11_TEXTURE3D_DESC1</b> structure to which <i>pDesc1</i> points. Arrays of 3D volume textures aren't supported.

For more information about this array size, see Remarks.

### -param ppTexture3D [out, optional]

Type: <b><a href="/windows/desktop/api/d3d11_3/nn-d3d11_3-id3d11texture3d1">ID3D11Texture3D1</a>**</b>

A pointer to a memory block that receives a pointer to a <a href="/windows/desktop/api/d3d11_3/nn-d3d11_3-id3d11texture3d1">ID3D11Texture3D1</a> interface for the created texture. Set this parameter to <b>NULL</b> to validate the other input parameters (the method will return <b>S_FALSE</b> if the other input parameters pass validation).

## -returns

Type: <b><a href="/windows/win32/com/structure-of-com-error-codes">HRESULT</a></b>

If the method succeeds, the return code is <b>S_OK</b>. See <a href="/windows/desktop/direct3d11/d3d11-graphics-reference-returnvalues">Direct3D 11 Return Codes</a> for failing error codes.

## -remarks

<b>CreateTexture3D1</b> creates a 3D texture resource, which can contain a number of 3D subresources. The number of textures is specified in the texture description. All textures in a resource must have the same format, size, and number of mipmap levels.

All resources are made up of one or more subresources. To load data into the texture, applications can supply the data initially as an array of <a href="/windows/desktop/api/d3d11/ns-d3d11-d3d11_subresource_data">D3D11_SUBRESOURCE_DATA</a> structures pointed to by <i>pInitialData</i>, or they can use one of the D3DX texture functions such as <a href="/windows/desktop/direct3d11/d3dx11createtexturefromfile">D3DX11CreateTextureFromFile</a>.

Each element of <i>pInitialData</i> provides all of the slices that are defined for a given miplevel. For example, for a 32 x 32 x 4 volume texture with a full mipmap chain, the array has the following 6 elements:

<ul>
<li>pInitialData[0] = 32x32 with 4 slices</li>
<li>pInitialData[1] = 16x16 with 2 slices</li>
<li>pInitialData[2] = 8x8 with 1 slice</li>
<li>pInitialData[3] = 4x4
with 1 slice</li>
<li>pInitialData[4] = 2x2
with 1 slice</li>
<li>pInitialData[5] = 1x1
with 1 slice</li>
</ul>

## -see-also

<a href="/windows/desktop/api/d3d11_3/nn-d3d11_3-id3d11device3">ID3D11Device3</a>