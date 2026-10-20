Source: [https://learn.microsoft.com/en-us/windows/win32/direct3d11/tiled-resources](<https://learn.microsoft.com/en-us/windows/win32/direct3d11/tiled-resources>)

# Tiled resources

Tiled resources can be thought of as large logical resources that use small amounts of physical memory.

This section describes why tiled resources are needed and how you create and use tiled resources.

## In this section



| Topic                                                                                   | Description                                                                                                                                                                                                                                         |
|-----------------------------------------------------------------------------------------|-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| [Why are tiled resources needed?](./why-are-tiled-resources-needed--a88623d672.md)<br/>       | Tiled resources are needed so less graphics processing unit (GPU) memory is wasted storing regions of surfaces that the application knows will not be accessed, and the hardware can understand how to filter across adjacent tiles.<br/>     |
| [Creating tiled resources](./creating-tiled-resources-0a11208f83.md)<br/>                     | Tiled resources are created by specifying the [**D3D11\_RESOURCE\_MISC\_TILED**](./ne-d3d11-d3d11_resource_misc_flag-f85f09a16f.md) flag when you create a resource.<br/>                                                                                          |
| [Tiled Resource APIs](./tiled-resource-apis-0f6e9397b0.md)<br/>                               | The APIs described in this section work with tiled resources and tile pool.<br/>                                                                                                                                                              |
| [Pipeline access to tiled resources](./pipeline-access-to-tiled-resources-d9163bdf11.md)<br/> | Tiled resources can be used in shader resource views (SRV), render target views (RTV), depth stencil views (DSV) and unordered access views (UAV), as well as some bind points where views aren't used, such as vertex buffer bindings. <br/> |
| [Tiled resources features tiers](./tiled-resources-features-tiers-904dd88d95.md)<br/>         | Direct3D 11.2 exposes tiled resources support in two tiers with the [**D3D11\_TILED\_RESOURCES\_TIER**](./ne-d3d11-d3d11_tiled_resources_tier-5ee336d92f.md) values. <br/>                                                                                         |



 

## Related topics

<dl> <dt>

[Resources](./overviews-direct3d-11-resources-87194d7e2a.md)
</dt> </dl>