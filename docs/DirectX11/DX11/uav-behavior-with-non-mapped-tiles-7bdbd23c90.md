Source: [https://learn.microsoft.com/en-us/windows/win32/direct3d11/uav-behavior-with-non-mapped-tiles](<https://learn.microsoft.com/en-us/windows/win32/direct3d11/uav-behavior-with-non-mapped-tiles>)

# UAV behavior with non-mapped tiles

Behavior of unordered access view (UAV) reads and writes depends on the level of hardware support. For a breakdown of requirements, see overall read and write behavior for [Tiled resources features tiers](./tiled-resources-features-tiers-904dd88d95.md). This section summarizes the ideal behavior.

Shader operations that read from a non-mapped tile in a UAV return 0 in all non-missing components of the format, and the default for missing components.

Shader operations that attempt to write to a non-mapped tile cause nothing to be written to the non-mapped area (while writes to a mapped area proceed). This ideal definition for write handling is not required by [Tier 2](./tier-2-a6fafc4219.md); writes to non-mapped tiles can end up in a cache that subsequent reads could pick up.

## Related topics

<dl> <dt>

[Pipeline access to tiled resources](./pipeline-access-to-tiled-resources-d9163bdf11.md)
</dt> </dl>