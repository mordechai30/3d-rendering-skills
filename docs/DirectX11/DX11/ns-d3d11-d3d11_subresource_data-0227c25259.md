Source: [https://learn.microsoft.com/en-us/windows/win32/api/D3D11/ns-d3d11-d3d11_subresource_data](<https://learn.microsoft.com/en-us/windows/win32/api/D3D11/ns-d3d11-d3d11_subresource_data>)

# D3D11_SUBRESOURCE_DATA structure


## -description

Specifies data for initializing a subresource.

## -struct-fields

### -field pSysMem

Type: <b>const void*</b>

Pointer to the initialization data.

### -field SysMemPitch

Type: <b><a href="/windows/desktop/WinProg/windows-data-types">UINT</a></b>

The distance (in bytes) from the beginning of one line of a texture to the next line.  
        System-memory pitch is used only for 2D and 3D texture data as it is has no meaning for the other resource types. Specify the distance from the first pixel of one 2D slice of a 3D texture to the first pixel of the next 2D slice in that texture in the <b>SysMemSlicePitch</b> member.

### -field SysMemSlicePitch

Type: <b><a href="/windows/desktop/WinProg/windows-data-types">UINT</a></b>

The distance (in bytes) from the beginning of one depth level to the next.  
        System-memory-slice pitch is only used for 3D texture data as it has no meaning for the other resource types.

## -remarks

This structure is used in calls to create buffers (<a href="/windows/desktop/api/d3d11/nf-d3d11-id3d11device-createbuffer">ID3D11Device::CreateBuffer</a>) and 
      textures (<a href="/windows/desktop/api/d3d11/nf-d3d11-id3d11device-createtexture1d">ID3D11Device::CreateTexture1D</a>, <a href="/windows/desktop/api/d3d11/nf-d3d11-id3d11device-createtexture2d">ID3D11Device::CreateTexture2D</a>, 
      and <a href="/windows/desktop/api/d3d11/nf-d3d11-id3d11device-createtexture3d">ID3D11Device::CreateTexture3D</a>). If the resource you create does not require a system-memory pitch or a system-memory-slice pitch, you can use those members to pass size information, which might help you when you debug a problem with creating a resource.

A subresource is a single mipmap-level surface. You can pass an array of subresources to one of the preceding methods to create the resource. A subresource can be 1D, 2D, or 3D. How you set the members of <b>D3D11_SUBRESOURCE_DATA</b> depend on whether the subresource is 1D, 2D, or 3D.



The x, y, and d values are 0-based indices and <b>BytesPerPixel</b> depends on the pixel format. For mipmapped 3D surfaces, the number of depth slices in each level is half the number of the previous level (minimum 1) and rounded down if dividing by two results in a non-whole number.

<div class="alert"><b>Note</b>  An application must not rely on <b>SysMemPitch</b> being exactly equal to the number of texels in a line times the size of a texel.
      In some cases, <b>SysMemPitch</b> will include padding to skip past additional data in a line.  This could be padding for alignment or 
      the texture could be a subsection of a larger texture.  For example, the <b>D3D11_SUBRESOURCE_DATA</b> structure could represent a 32 by 32 subsection of a 128 by 128 texture.  
      The value for <b>SysMemSlicePitch</b> will reflect any padding included in <b>SysMemPitch</b>.</div>
<div> </div>

## -see-also

<a href="/windows/desktop/direct3d11/d3d11-graphics-reference-resource-structures">Resource Structures</a>