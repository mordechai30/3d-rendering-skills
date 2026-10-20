Source: [https://learn.microsoft.com/en-us/windows/win32/api/D3D11/nf-d3d11-d3d11calcsubresource](<https://learn.microsoft.com/en-us/windows/win32/api/D3D11/nf-d3d11-d3d11calcsubresource>)

# D3D11CalcSubresource function


## -description

Calculates a subresource index for a texture.

## -parameters

### -param MipSlice

Type: <b><a href="/windows/desktop/WinProg/windows-data-types">UINT</a></b>

A zero-based index for the mipmap level to address; 0 indicates the first, most detailed mipmap level.

### -param ArraySlice

Type: <b><a href="/windows/desktop/WinProg/windows-data-types">UINT</a></b>

The zero-based index for the array level to address; always use 0 for volume (3D) textures.

### -param MipLevels

Type: <b><a href="/windows/desktop/WinProg/windows-data-types">UINT</a></b>

Number of mipmap levels in the resource.

## -returns

Type: <b><a href="/windows/desktop/WinProg/windows-data-types">UINT</a></b>

The index which equals MipSlice + (ArraySlice * MipLevels).

## -remarks

A buffer is an unstructured resource and is therefore defined as containing a single subresource. APIs that take buffers do not need a subresource index.
          A texture on the other hand is highly structured. Each texture object may contain one or more subresources depending on the size of the array and the
          number of mipmap levels.
        

For volume (3D) textures, all slices for a given mipmap level are a single subresource index.

## -see-also

<a href="/windows/desktop/direct3d11/d3d11-graphics-reference-d3d11-core-functions">Core Functions</a>



<a href="/windows/desktop/direct3d11/d3d11-graphics-reference-resource-functions">Resource Functions</a>