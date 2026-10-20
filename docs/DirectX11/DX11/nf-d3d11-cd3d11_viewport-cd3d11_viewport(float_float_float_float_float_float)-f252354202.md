Source: [https://learn.microsoft.com/en-us/windows/win32/api/d3d11/nf-d3d11-cd3d11_viewport-cd3d11_viewport(float_float_float_float_float_float)](<https://learn.microsoft.com/en-us/windows/win32/api/d3d11/nf-d3d11-cd3d11_viewport-cd3d11_viewport(float_float_float_float_float_float)>)

# CD3D11_VIEWPORT::CD3D11_VIEWPORT(FLOAT,FLOAT,FLOAT,FLOAT,FLOAT,FLOAT)


## -description

Instantiates a new instance of a <a href="/previous-versions/windows/desktop/legacy/jj151722(v=vs.85)">CD3D11_VIEWPORT</a> structure that is initialized with <a href="/windows/desktop/api/d3d11/ns-d3d11-d3d11_viewport">D3D11_VIEWPORT</a> values.

## -parameters

### -param topLeftX

Type: <b><a href="/windows/desktop/WinProg/windows-data-types">FLOAT</a></b>

X position of the left hand side of the viewport. Ranges between D3D11_VIEWPORT_BOUNDS_MIN and D3D11_VIEWPORT_BOUNDS_MAX.

### -param topLeftY

Type: <b><a href="/windows/desktop/WinProg/windows-data-types">FLOAT</a></b>

Y position of the top of the viewport. Ranges between D3D11_VIEWPORT_BOUNDS_MIN and D3D11_VIEWPORT_BOUNDS_MAX.

### -param width

Type: <b><a href="/windows/desktop/WinProg/windows-data-types">FLOAT</a></b>

Width of the viewport.

### -param height

Type: <b><a href="/windows/desktop/WinProg/windows-data-types">FLOAT</a></b>

Height of the viewport.

### -param minDepth

Type: <b><a href="/windows/desktop/WinProg/windows-data-types">FLOAT</a></b>

Minimum depth of the viewport. Ranges between 0 and 1.

### -param maxDepth

Type: <b><a href="/windows/desktop/WinProg/windows-data-types">FLOAT</a></b>

Maximum depth of the viewport. Ranges between 0 and 1.

## -see-also

<a href="/previous-versions/windows/desktop/legacy/jj151722(v=vs.85)">CD3D11_VIEWPORT</a>