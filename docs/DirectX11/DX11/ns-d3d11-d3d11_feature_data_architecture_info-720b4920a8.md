Source: [https://learn.microsoft.com/en-us/windows/win32/api/D3D11/ns-d3d11-d3d11_feature_data_architecture_info](<https://learn.microsoft.com/en-us/windows/win32/api/D3D11/ns-d3d11-d3d11_feature_data_architecture_info>)

# D3D11_FEATURE_DATA_ARCHITECTURE_INFO structure


## -description

<div class="alert"><b>Note</b>  This structure is supported by the Direct3D 11.1 runtime, which is available on Windows 8 and later operating systems.</div><div> </div>Describes information about Direct3D 11.1 adapter architecture.

## -struct-fields

### -field TileBasedDeferredRenderer

Specifies whether a rendering device batches rendering commands and performs multipass rendering into tiles or bins over a render area. Certain API usage patterns that are fine for TileBasedDefferredRenderers (TBDRs) can perform worse on non-TBDRs and vice versa.  Applications that are careful about rendering can be friendly to both TBDR and non-TBDR architectures. <b>TRUE</b> if the rendering device batches rendering commands and <b>FALSE</b> otherwise.

## -see-also

<a href="/windows/desktop/direct3d11/d3d11-graphics-reference-d3d11-core-structures">Core Structures</a>



<a href="/windows/desktop/api/d3d11/ne-d3d11-d3d11_feature">D3D11_FEATURE</a>