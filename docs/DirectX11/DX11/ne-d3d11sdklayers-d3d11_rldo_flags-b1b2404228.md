Source: [https://learn.microsoft.com/en-us/windows/win32/api/D3D11SDKLayers/ne-d3d11sdklayers-d3d11_rldo_flags](<https://learn.microsoft.com/en-us/windows/win32/api/D3D11SDKLayers/ne-d3d11sdklayers-d3d11_rldo_flags>)

# D3D11_RLDO_FLAGS enumeration


## -description

Options for the amount of information to report about a device object's lifetime.

## -enum-fields

### -field D3D11_RLDO_SUMMARY:0x1

Specifies to obtain a summary about a device object's lifetime.

### -field D3D11_RLDO_DETAIL:0x2

Specifies to obtain detailed information about a device object's lifetime.

### -field D3D11_RLDO_IGNORE_INTERNAL:0x4

This flag indicates to ignore objects which have no external refcounts keeping them alive. D3D objects are printed using an external refcount and an internal refcount. Typically, all objects are printed. This flag means ignore the objects whose external refcount is 0, because the application is not responsible for keeping them alive.

## -remarks

This enumeration is used by <a href="/windows/desktop/api/d3d11sdklayers/nf-d3d11sdklayers-id3d11debug-reportlivedeviceobjects">ID3D11Debug::ReportLiveDeviceObjects</a>.
        

Several inline functions exist to combine the options using operators, see the D3D11SDKLayers.h header file for details.

## -see-also

<a href="/windows/desktop/direct3d11/d3d11-graphics-reference-d3d11-layer-enums">Core Enumerations</a>