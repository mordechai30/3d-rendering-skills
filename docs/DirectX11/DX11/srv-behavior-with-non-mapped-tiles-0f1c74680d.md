Source: [https://learn.microsoft.com/en-us/windows/win32/direct3d11/srv-behavior-with-non-mapped-tiles](<https://learn.microsoft.com/en-us/windows/win32/direct3d11/srv-behavior-with-non-mapped-tiles>)

# SRV behavior with non-mapped tiles

Behavior of shader resource view (SRV) reads that involve non-mapped tiles depends on the level of hardware support. For a breakdown of requirements, see read behavior for [Tiled resources features tiers](./tiled-resources-features-tiers-904dd88d95.md). This section summarizes the ideal behavior, which [Tier 2](./tier-2-a6fafc4219.md) requires.

Consider a texture filter operation that reads from a set of texels in an SRV. Texels that fall on non-mapped tiles contribute 0 in all non-missing components of the format (and the default for missing components) into the overall filter operation alongside contributions from mapped texels. The texels are all weighted and combined together independent of whether the data came from mapped or non-mapped tiles.

Some first generation [Tier 2](./tier-2-a6fafc4219.md) level hardware does not meet this spec requirement and returns the 0 with defaults described preceding as the overall filter result if any texels (with nonzero weight) fall on non-mapped tiles. No other hardware will be allowed to miss the requirement to include all (nonzero weight) texels in the filter.

## Related topics

<dl> <dt>

[Pipeline access to tiled resources](./pipeline-access-to-tiled-resources-d9163bdf11.md)
</dt> </dl>