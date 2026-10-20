Source: [https://learn.microsoft.com/en-us/windows/win32/api/D3D11SDKLayers/ne-d3d11sdklayers-d3d11_shader_tracking_options](<https://learn.microsoft.com/en-us/windows/win32/api/D3D11SDKLayers/ne-d3d11sdklayers-d3d11_shader_tracking_options>)

# D3D11_SHADER_TRACKING_OPTIONS enumeration


## -description

Options that specify how to perform shader debug tracking.

## -enum-fields

### -field D3D11_SHADER_TRACKING_OPTION_IGNORE:0

No debug tracking is performed.

### -field D3D11_SHADER_TRACKING_OPTION_TRACK_UNINITIALIZED:0x1

Track the reading of uninitialized data.

### -field D3D11_SHADER_TRACKING_OPTION_TRACK_RAW:0x2

Track read-after-write hazards.

### -field D3D11_SHADER_TRACKING_OPTION_TRACK_WAR:0x4

Track write-after-read hazards.

### -field D3D11_SHADER_TRACKING_OPTION_TRACK_WAW:0x8

Track write-after-write hazards.

### -field D3D11_SHADER_TRACKING_OPTION_ALLOW_SAME:0x10

Track that hazards are allowed in which data is written but the value does not change.

### -field D3D11_SHADER_TRACKING_OPTION_TRACK_ATOMIC_CONSISTENCY:0x20

Track that only one type of atomic operation is used on an address.

### -field D3D11_SHADER_TRACKING_OPTION_TRACK_RAW_ACROSS_THREADGROUPS:0x40

Track read-after-write hazards across thread groups.

### -field D3D11_SHADER_TRACKING_OPTION_TRACK_WAR_ACROSS_THREADGROUPS:0x80

Track write-after-read hazards across thread groups.

### -field D3D11_SHADER_TRACKING_OPTION_TRACK_WAW_ACROSS_THREADGROUPS:0x100

Track write-after-write hazards across thread groups.

### -field D3D11_SHADER_TRACKING_OPTION_TRACK_ATOMIC_CONSISTENCY_ACROSS_THREADGROUPS:0x200

Track that only one type of atomic operation is used on an address across thread groups.

### -field D3D11_SHADER_TRACKING_OPTION_UAV_SPECIFIC_FLAGS

Track hazards that are specific to unordered access views (UAVs).

### -field D3D11_SHADER_TRACKING_OPTION_ALL_HAZARDS

Track all hazards.

### -field D3D11_SHADER_TRACKING_OPTION_ALL_HAZARDS_ALLOWING_SAME

Track all hazards and track that hazards are allowed in which data is written but the value does not change.

### -field D3D11_SHADER_TRACKING_OPTION_ALL_OPTIONS

All of the preceding tracking options are set except <b>D3D11_SHADER_TRACKING_OPTION_IGNORE</b>.

## -remarks

This enumeration is used by the following methods:
        

<ul>
<li>
<a href="/windows/desktop/api/d3d11sdklayers/nf-d3d11sdklayers-id3d11refdefaulttrackingoptions-settrackingoptions">ID3D11RefDefaultTrackingOptions::SetTrackingOptions</a>
</li>
<li>
<a href="/windows/desktop/api/d3d11sdklayers/nf-d3d11sdklayers-id3d11reftrackingoptions-settrackingoptions">ID3D11RefTrackingOptions::SetTrackingOptions</a>
</li>
<li>
<a href="/windows/desktop/api/d3d11sdklayers/nf-d3d11sdklayers-id3d11tracingdevice-setshadertrackingoptions">ID3D11TracingDevice::SetShaderTrackingOptions</a>
</li>
<li>
<a href="/windows/desktop/api/d3d11sdklayers/nf-d3d11sdklayers-id3d11tracingdevice-setshadertrackingoptionsbytype">ID3D11TracingDevice::SetShaderTrackingOptionsByType</a>
</li>
</ul>
<div class="alert"><b>Note</b>  This API requires the Windows Software Development Kit (SDK) for Windows 8.
      </div>
<div> </div>

## -see-also

<a href="/windows/desktop/direct3d11/d3d11-graphics-reference-d3d11-layer-enums">Layer Enumerations</a>