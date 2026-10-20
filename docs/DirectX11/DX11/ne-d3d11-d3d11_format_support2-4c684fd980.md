Source: [https://learn.microsoft.com/en-us/windows/win32/api/D3D11/ne-d3d11-d3d11_format_support2](<https://learn.microsoft.com/en-us/windows/win32/api/D3D11/ne-d3d11-d3d11_format_support2>)

# D3D11_FORMAT_SUPPORT2 enumeration


## -description

Unordered resource support options for a compute shader resource (see <a href="/windows/desktop/api/d3d11/nf-d3d11-id3d11device-checkfeaturesupport">ID3D11Device::CheckFeatureSupport</a>).

## -enum-fields

### -field D3D11_FORMAT_SUPPORT2_UAV_ATOMIC_ADD:0x1

Format supports atomic add.

### -field D3D11_FORMAT_SUPPORT2_UAV_ATOMIC_BITWISE_OPS:0x2

Format supports atomic bitwise operations.

### -field D3D11_FORMAT_SUPPORT2_UAV_ATOMIC_COMPARE_STORE_OR_COMPARE_EXCHANGE:0x4

Format supports atomic compare with store or exchange.

### -field D3D11_FORMAT_SUPPORT2_UAV_ATOMIC_EXCHANGE:0x8

Format supports atomic exchange.

### -field D3D11_FORMAT_SUPPORT2_UAV_ATOMIC_SIGNED_MIN_OR_MAX:0x10

Format supports atomic min and max.

### -field D3D11_FORMAT_SUPPORT2_UAV_ATOMIC_UNSIGNED_MIN_OR_MAX:0x20

Format supports atomic unsigned min and max.

### -field D3D11_FORMAT_SUPPORT2_UAV_TYPED_LOAD:0x40

Format supports a typed load.

### -field D3D11_FORMAT_SUPPORT2_UAV_TYPED_STORE:0x80

Format supports a typed store.

### -field D3D11_FORMAT_SUPPORT2_OUTPUT_MERGER_LOGIC_OP:0x100

Format supports logic operations in blend state.

<b>Direct3D 11:  </b>This value is not supported until Direct3D 11.1.

### -field D3D11_FORMAT_SUPPORT2_TILED:0x200

Format supports tiled resources.

<b>Direct3D 11:  </b>This value is not supported until Direct3D 11.2.

### -field D3D11_FORMAT_SUPPORT2_SHAREABLE:0x400

Format supports shareable resources.
              <div class="alert"><b>Note</b>  <a href="/windows/desktop/api/dxgiformat/ne-dxgiformat-dxgi_format">DXGI_FORMAT_R8G8B8A8_UNORM</a> and <b>DXGI_FORMAT_R8G8B8A8_UNORM_SRGB</b> are never shareable when using feature level 9, even if the device indicates optional feature support for <b>D3D11_FORMAT_SUPPORT_SHAREABLE</b>.
                Attempting to create shared resources with DXGI formats <b>DXGI_FORMAT_R8G8B8A8_UNORM</b> and <b>DXGI_FORMAT_R8G8B8A8_UNORM_SRGB</b> will always fail unless the feature level is 10_0 or higher.
              </div>
<div> </div>


<b>Direct3D 11:  </b>This value is not supported until Direct3D 11.2.

### -field D3D11_FORMAT_SUPPORT2_MULTIPLANE_OVERLAY:0x4000

Format supports multi-plane overlays.

## -see-also

<a href="/windows/desktop/direct3d11/d3d11-graphics-reference-d3d11-core-enums">Core Enumerations</a>