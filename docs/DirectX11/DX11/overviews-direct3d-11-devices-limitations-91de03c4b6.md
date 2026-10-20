Source: [https://learn.microsoft.com/en-us/windows/win32/direct3d11/overviews-direct3d-11-devices-limitations](<https://learn.microsoft.com/en-us/windows/win32/direct3d11/overviews-direct3d-11-devices-limitations>)

# Limitations Creating WARP and Reference Devices

Some limitations exist for creating WARP and Reference devices in Direct3D 10.1 and Direct3D 11.0. This topic discusses those limitations.

The D3D10\_DRIVER\_TYPE\_WARP and D3D10\_DRIVER\_TYPE\_REFERENCE driver types are not supported on the D3D10\_FEATURE\_LEVEL\_9\_1 through D3D10\_FEATURE\_LEVEL\_9\_3 feature levels in Direct3D 10.1. Additionally, the D3D\_DRIVER\_TYPE\_WARP driver type is not supported on D3D\_FEATURE\_LEVEL\_11\_0 in Direct3D 11.0. That is, when you call [**D3D10CreateDevice1**](/windows/desktop/api/d3d10_1/nf-d3d10_1-d3d10createdevice1) to create a Direct3D 10.1 device or when you call [**D3D11CreateDevice**](./nf-d3d11-d3d11createdevice-fbcd3f07e1.md) to create a Direct3D 11.0 device, if you specify a combination of one of these driver types with one of these feature levels in the call, the call is invalid. Only the following combinations of feature levels, runtimes, and driver types are valid for WARP and Reference devices:

-   D3D\_DRIVER\_TYPE\_WARP on all feature levels in Direct3D 11.1, which Windows 8 includes

    D3D\_DRIVER\_TYPE\_REFERENCE on all feature levels in Direct3D 11.1

    When you call [**D3D11CreateDevice**](./nf-d3d11-d3d11createdevice-fbcd3f07e1.md) to create a Direct3D 11.1 device, the call is valid if you specify a combination of one of these driver types with one of these feature levels.

-   D3D\_DRIVER\_TYPE\_WARP on D3D\_FEATURE\_LEVEL\_9\_1 through D3D\_FEATURE\_LEVEL\_10\_1 feature levels in Direct3D 11

    D3D\_DRIVER\_TYPE\_REFERENCE on D3D\_FEATURE\_LEVEL\_9\_1 through D3D\_FEATURE\_LEVEL\_11\_0 feature levels in Direct3D 11

    When you call [**D3D11CreateDevice**](./nf-d3d11-d3d11createdevice-fbcd3f07e1.md) to create a Direct3D 11 device, the call is valid if you specify a combination of one of these driver types with one of these feature levels.

-   D3D10\_DRIVER\_TYPE\_WARP and D3D10\_DRIVER\_TYPE\_REFERENCE on D3D10\_FEATURE\_LEVEL\_10\_0 through D3D10\_FEATURE\_LEVEL\_10\_1 feature levels in Direct3D 10.1

    When you call [**D3D10CreateDevice1**](/windows/desktop/api/d3d10_1/nf-d3d10_1-d3d10createdevice1) to create a Direct3D 10.1 device, the call is valid if you specify a combination of one of these driver types with one of these feature levels.

## Related topics

<dl> <dt>

[Devices](./overviews-direct3d-11-devices-8464b8d294.md)
</dt> <dt>

[Introduction to Direct3D 11 on Downlevel Hardware](./overviews-direct3d-11-devices-downlevel-intro-f595280e88.md)
</dt> <dt>

[How To: Create a WARP Device](./overviews-direct3d-11-devices-create-warp-1c4142d50e.md)
</dt> <dt>

[How To: Create a Reference Device](./overviews-direct3d-11-devices-create-ref-0592e23b64.md)
</dt> <dt>

[**D3D10\_DRIVER\_TYPE**](/windows/desktop/api/d3d10misc/ne-d3d10misc-d3d10_driver_type)
</dt> <dt>

[**D3D10\_FEATURE\_LEVEL1**](/windows/desktop/api/d3d10_1/ne-d3d10_1-d3d10_feature_level1)
</dt> <dt>

[**D3D\_DRIVER\_TYPE**](./ne-d3dcommon-d3d_driver_type-24df852fcc.md)
</dt> <dt>

[**D3D\_FEATURE\_LEVEL**](./ne-d3dcommon-d3d_feature_level-fa6ac3128b.md)
</dt> </dl>