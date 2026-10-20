Source: [https://learn.microsoft.com/en-us/windows/win32/direct3d11/tiled-resources-features-tiers](<https://learn.microsoft.com/en-us/windows/win32/direct3d11/tiled-resources-features-tiers>)

# Tiled resources features tiers

Direct3D 11.2 exposes tiled resources support in two tiers with the [**D3D11\_TILED\_RESOURCES\_TIER**](./ne-d3d11-d3d11_tiled_resources_tier-5ee336d92f.md) values.

To query whether the hardware and driver support tiled resources and at what tier level, pass the [**D3D11\_FEATURE\_D3D11\_OPTIONS1**](./ne-d3d11-d3d11_feature-a05a7560bc.md) value to the *Feature* parameter of [**ID3D11Device::CheckFeatureSupport**](./nf-d3d11-id3d11device-checkfeaturesupport-ec5826ac8e.md). Also, pass a pointer to the [**D3D11\_FEATURE\_DATA\_D3D11\_OPTIONS1**](./ns-d3d11-d3d11_feature_data_d3d11_options1-7d38ff7774.md) structure to the *pFeatureSupportData* parameter, and pass the size of the **D3D11\_FEATURE\_DATA\_D3D11\_OPTIONS1** structure to the *FeatureSupportDataSize* parameter. **CheckFeatureSupport** returns the tier level as a [**D3D11\_TILED\_RESOURCES\_TIER**](./ne-d3d11-d3d11_tiled_resources_tier-5ee336d92f.md) value in the **TiledResourcesTier** member of **D3D11\_FEATURE\_DATA\_D3D11\_OPTIONS1**.

This section describes these two tiers.

## In this section



| Topic                           | Description                                       |
|---------------------------------|---------------------------------------------------|
| [Tier 1](./tier-1-f004749ec1.md)<br/> | This section describes tier 1 support.<br/> |
| [Tier 2](./tier-2-a6fafc4219.md)<br/> | This section describes tier 2 support.<br/> |



 

## Related topics

<dl> <dt>

[Tiled resources](./tiled-resources-8d4a7f2d4e.md)
</dt> </dl>