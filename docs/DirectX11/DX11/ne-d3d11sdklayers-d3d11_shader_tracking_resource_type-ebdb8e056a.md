Source: [https://learn.microsoft.com/en-us/windows/win32/api/D3D11SDKLayers/ne-d3d11sdklayers-d3d11_shader_tracking_resource_type](<https://learn.microsoft.com/en-us/windows/win32/api/D3D11SDKLayers/ne-d3d11sdklayers-d3d11_shader_tracking_resource_type>)

# D3D11_SHADER_TRACKING_RESOURCE_TYPE enumeration


## -description

Indicates which resource types to track.

## -enum-fields

### -field D3D11_SHADER_TRACKING_RESOURCE_TYPE_NONE:0

No resource types are tracked.

### -field D3D11_SHADER_TRACKING_RESOURCE_TYPE_UAV_DEVICEMEMORY:1

Track device memory that is created with unordered access view (UAV) bind flags.

### -field D3D11_SHADER_TRACKING_RESOURCE_TYPE_NON_UAV_DEVICEMEMORY:2

Track device memory that is created without UAV bind flags.

### -field D3D11_SHADER_TRACKING_RESOURCE_TYPE_ALL_DEVICEMEMORY:3

Track all device memory.

### -field D3D11_SHADER_TRACKING_RESOURCE_TYPE_GROUPSHARED_MEMORY:4

Track all shaders that use group shared memory.

### -field D3D11_SHADER_TRACKING_RESOURCE_TYPE_ALL_SHARED_MEMORY:5

Track all device memory except device memory that is created without UAV bind flags.

### -field D3D11_SHADER_TRACKING_RESOURCE_TYPE_GROUPSHARED_NON_UAV:6

Track all device memory except device memory that is created with UAV bind flags.

### -field D3D11_SHADER_TRACKING_RESOURCE_TYPE_ALL:7

Track all memory on the device.

## -remarks

The <a href="/windows/desktop/api/d3d11sdklayers/nf-d3d11sdklayers-id3d11tracingdevice-setshadertrackingoptionsbytype">ID3D11TracingDevice::SetShaderTrackingOptionsByType</a> or <a href="/windows/desktop/api/d3d11sdklayers/nf-d3d11sdklayers-id3d11refdefaulttrackingoptions-settrackingoptions">ID3D11RefDefaultTrackingOptions::SetTrackingOptions</a> method tracks a specific type of resource.

<div class="alert"><b>Note</b>  This API requires the Windows Software Development Kit (SDK) for Windows 8.</div>
<div> </div>

## -see-also

<a href="/windows/desktop/direct3d11/d3d11-graphics-reference-d3d11-layer-enums">Layer Enumerations</a>