Source: [https://learn.microsoft.com/en-us/windows/win32/direct3d11/overviews-direct3d-11-devices-downlevel-get](<https://learn.microsoft.com/en-us/windows/win32/direct3d11/overviews-direct3d-11-devices-downlevel-get>)

# How To: Get the Device Feature Level

This topics shows how to get the highest [feature level](./overviews-direct3d-11-devices-downlevel-intro-f595280e88.md) supported by a [device](./overviews-direct3d-11-devices-intro-469d7832b7.md). Direct3D 11 devices support a fixed set of feature levels that are defined in the [**D3D\_FEATURE\_LEVEL**](./ne-d3dcommon-d3d_feature_level-fa6ac3128b.md) enumeration. When you know the highest [feature level](./overviews-direct3d-11-devices-downlevel-intro-f595280e88.md) supported by a device, you can run code paths that are appropriate for that device.

**To get the device feature level**

1.  Call either the [**D3D11CreateDevice**](./nf-d3d11-d3d11createdevice-fbcd3f07e1.md) function or the [**D3D11CreateDeviceAndSwapChain**](./nf-d3d11-d3d11createdeviceandswapchain-5744e33d11.md) functions while specifying **NULL** for the *ppDevice* parameter. You can do this before device creation.

    \- or -

    Call [**ID3D11Device::GetFeatureLevel**](./nf-d3d11-id3d11device-getfeaturelevel-666fc5c40d.md) after device creation.

2.  Examine the value of the returned [**D3D\_FEATURE\_LEVEL**](./ne-d3dcommon-d3d_feature_level-fa6ac3128b.md) enumeration from the last step to determine the supported feature level.

The following code example demonstrates how to determine the highest supported feature level by calling the [**D3D11CreateDevice**](./nf-d3d11-d3d11createdevice-fbcd3f07e1.md) function. **D3D11CreateDevice** stores the highest supported feature level in the FeatureLevel variable. You can use this code to examine the value of the [**D3D\_FEATURE\_LEVEL**](./ne-d3dcommon-d3d_feature_level-fa6ac3128b.md) enumerated type that **D3D11CreateDevice** returns. Note that this code lists all feature levels explicitly (for Direct3D 11.1 and Direct3D 11.2).

> [!Note]  
> If the Direct3D 11.1 runtime is present on the computer and *pFeatureLevels* is set to **NULL**, this function won't create a [**D3D\_FEATURE\_LEVEL\_11\_1**](./ne-d3dcommon-d3d_feature_level-fa6ac3128b.md) device. To create a **D3D\_FEATURE\_LEVEL\_11\_1** device, you must explicitly provide a **D3D\_FEATURE\_LEVEL** array that includes **D3D\_FEATURE\_LEVEL\_11\_1**. If you provide a **D3D\_FEATURE\_LEVEL** array that contains **D3D\_FEATURE\_LEVEL\_11\_1** on a computer that doesn't have the Direct3D 11.1 runtime installed, this function immediately fails with E\_INVALIDARG.

 


```C++
HRESULT hr = E_FAIL;
D3D_FEATURE_LEVEL MaxSupportedFeatureLevel = D3D_FEATURE_LEVEL_9_1;
D3D_FEATURE_LEVEL FeatureLevels[] = {
    D3D_FEATURE_LEVEL_11_1,
    D3D_FEATURE_LEVEL_11_0,
    D3D_FEATURE_LEVEL_10_1,
    D3D_FEATURE_LEVEL_10_0,
    D3D_FEATURE_LEVEL_9_3,
    D3D_FEATURE_LEVEL_9_2,
    D3D_FEATURE_LEVEL_9_1
    };

hr = D3D11CreateDevice(
    NULL,
    D3D_DRIVER_TYPE_HARDWARE,
    NULL, 
    0, 
    &FeatureLevels, 
    ARRAYSIZE(FeatureLevels), 
    D3D11_SDK_VERSION, 
    NULL, 
    &MaxSupportedFeatureLevel, 
    NULL 
    );

if(FAILED(hr))
{
    return hr;
}
```



The [10Level9 Reference](./d3d11-graphics-reference-10level9-71856f59bf.md) section lists the differences between how various [**ID3D11Device**](./nn-d3d11-id3d11device-6e49ef4b9e.md) and [**ID3D11DeviceContext**](./nn-d3d11-id3d11devicecontext-abe911f651.md) methods behave at various 10Level9 feature levels.

## Related topics

<dl> <dt>

[Direct3D 11 on Downlevel Hardware](./overviews-direct3d-11-devices-downlevel-366ef41a88.md)
</dt> <dt>

[How to Use Direct3D 11](./how-to-use-direct3d-11-112ea0ccbf.md)
</dt> </dl>