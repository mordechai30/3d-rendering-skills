Source: [https://learn.microsoft.com/en-us/windows/win32/direct3d11/unified-memory-architecture](<https://learn.microsoft.com/en-us/windows/win32/direct3d11/unified-memory-architecture>)

# Unified Memory Architecture

Querying for whether Unified Memory Architecture (UMA) is supported can help determine how to handle some resources.

A boolean, set by the driver, can be read from the [**D3D11\_FEATURE\_DATA\_D3D11\_OPTIONS2**](./ns-d3d11-d3d11_feature_data_d3d11_options2-c4464cbb03.md) structure to determine if the hardware supports UMA.

Applications running on UMA may want to have more resources with CPU access enabled than if it is not available. UMA enables applications to avoiding copying resource data around, instead of staying efficient solely for non-UMA graphics adapters. [Direct3D 11.3 Features](./direct3d-11-3-features-87cd0e6b8b.md)

## Related topics

<dl> <dt>

[Direct3D 11.3 Features](./direct3d-11-3-features-87cd0e6b8b.md)
</dt> </dl>