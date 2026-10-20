Source: [https://learn.microsoft.com/en-us/windows/win32/api/D3D11/ns-d3d11-d3d11_box](<https://learn.microsoft.com/en-us/windows/win32/api/D3D11/ns-d3d11-d3d11_box>)

# D3D11_BOX structure


## -description

Defines a 3D box.

## -struct-fields

### -field left

Type: <b><a href="/windows/desktop/WinProg/windows-data-types">UINT</a></b>

The x position of the left hand side of the box.

### -field top

Type: <b><a href="/windows/desktop/WinProg/windows-data-types">UINT</a></b>

The y position of the top of the box.

### -field front

Type: <b><a href="/windows/desktop/WinProg/windows-data-types">UINT</a></b>

The z position of the front of the box.

### -field right

Type: <b><a href="/windows/desktop/WinProg/windows-data-types">UINT</a></b>

The x position of the right hand side of the box.

### -field bottom

Type: <b><a href="/windows/desktop/WinProg/windows-data-types">UINT</a></b>

The y position of the bottom of the box.

### -field back

Type: <b><a href="/windows/desktop/WinProg/windows-data-types">UINT</a></b>

The z position of the back of the box.

## -remarks

The following diagram shows a 3D box, where the origin is the left, front, top corner.

<img alt="Diagram of a 3D box, where the origin is the left, front, top corner" src="./images/D3D10_box.png"/>

The values for <b>right</b>, <b>bottom</b>, and <b>back</b> are each one pixel past the end of the pixels that are included in the box region.  That is, the values for <b>left</b>, <b>top</b>, and <b>front</b> are included in the box region while the values for right, bottom, and back are excluded from the box region. For example, for a box that is one pixel wide, (right - left) == 1; the box region includes the left pixel but not the right pixel.

Coordinates of a box are in bytes for buffers and in texels for textures.

## -see-also

<a href="/windows/desktop/direct3d11/d3d11-graphics-reference-d3d11-core-structures">Core Structures</a>