Source: [https://learn.microsoft.com/en-us/windows/win32/api/d3dcommon/ne-d3dcommon-d3d_include_type](<https://learn.microsoft.com/en-us/windows/win32/api/d3dcommon/ne-d3dcommon-d3d_include_type>)

# D3D_INCLUDE_TYPE enumeration


## -description

Values that indicate the location of a shader #include file. 

> [!NOTE]
> For programming with Direct3D 10, this API has a type alias that begins `D3D10_` instead of `D3D_`. These Direct3D 10 type aliases are defined in `d3d10.h`, `d3d10misc.h`, and `d3d10shader.h`.

## -enum-fields

### -field D3D_INCLUDE_LOCAL:0

The local directory.

### -field D3D_INCLUDE_SYSTEM

The system directory.

### -field D3D10_INCLUDE_LOCAL

The local directory.

### -field D3D10_INCLUDE_SYSTEM

The system directory.

### -field D3D_INCLUDE_FORCE_DWORD:0x7fffffff

Forces this enumeration to compile to 32 bits in size. Without this value, some compilers would allow this enumeration to compile to a size other than 32 bits. 

Do not use this value.

## -remarks

You pass a <b>D3D_INCLUDE_TYPE</b>-typed value to the  <i>IncludeType</i> parameter in a call to the  <a href="/windows/desktop/api/d3dcommon/nf-d3dcommon-id3dinclude-open">ID3DInclude::Open</a> method to indicate the location of the #include file.

## -see-also

<a href="/windows/desktop/direct3d11/d3d11-graphics-reference-d3d11-common-enumerations">Common Version Enumerations</a>



<a href="/windows/desktop/api/d3dcommon/ne-d3dcommon-d3d_include_type">D3D_INCLUDE_TYPE</a>



<a href="/windows/desktop/api/d3dcommon/nf-d3dcommon-id3dinclude-open">ID3DInclude::Open</a>