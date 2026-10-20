Source: [https://learn.microsoft.com/en-us/windows/win32/direct3d11/overviews-direct3d-11-devices-downlevel](<https://learn.microsoft.com/en-us/windows/win32/direct3d11/overviews-direct3d-11-devices-downlevel>)

# Direct3D 11 on Downlevel Hardware

This section discusses how Direct3D 11 is designed to support both new and existing hardware, from DirectX 9 to DirectX 11.

This diagram shows how Direct3D 11 supports new and existing hardware.

![diagram of the hardware that direct3d 11 supports](<overviews-direct3d-11-devices-downlevel/78f507f817a31ee0c5a5297d.png>)

With Direct3D 11, a new paradigm is introduced called feature levels. A feature level is a well defined set of GPU functionality. Using a feature level, you can target a Direct3D application to run on a downlevel version of Direct3D hardware.

The [10Level9 Reference](./d3d11-graphics-reference-10level9-71856f59bf.md) section lists the differences between how various [**ID3D11Device**](./nn-d3d11-id3d11device-6e49ef4b9e.md) and [**ID3D11DeviceContext**](./nn-d3d11-id3d11devicecontext-abe911f651.md) methods behave at various 10Level9 feature levels.


## In this section



| Topic                                                                                                                  | Description                                                                                                                                                                    |
|------------------------------------------------------------------------------------------------------------------------|--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| [Direct3D feature levels](./overviews-direct3d-11-devices-downlevel-intro-f595280e88.md)<br/>                                | This topic discusses Direct3D feature levels.<br/>                                                                                                                       |
| [Exceptions](./overviews-direct3d-11-devices-downlevel-exceptions-a64098e562.md)<br/>                                        | This topic describes exceptions when using Direct3D 11 on downlevel hardware. <br/>                                                                                      |
| [Compute Shaders on Downlevel Hardware](./overviews-direct3d-11-devices-downlevel-compute-shaders-2f4958c245.md)<br/>        | This topic discusses how to make use of [compute shaders](./direct3d-11-advanced-stages-compute-shader-5ea3c0666f.md) in a Direct3D 11 app on Direct3D 10 hardware.<br/>             |
| [Preventing Unwanted NULL Pixel Shader SRVs](./overviews-direct3d-11-devices-downlevel-prevent-null-srvs-1039063258.md)<br/> | This topic discusses how to work around the driver receiving **NULL** shader-resource views (SRVs) even when non-**NULL** SRVs are bound to the pixel shader stage.<br/> |



 

## How to topics about feature levels



| Topic                                                                                                                                                                                                                                                                   | Description                            |
|-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|----------------------------------------|
| <span id="How_To__Get_the_Device_Feature_Level"></span><span id="how_to__get_the_device_feature_level"></span><span id="HOW_TO__GET_THE_DEVICE_FEATURE_LEVEL"></span>[How To: Get the Device Feature Level](./overviews-direct3d-11-devices-downlevel-get-3859c50317.md)<br/> | How to get a feature level.<br/> |



 

## Related topics

<dl> <dt>

[Devices](./overviews-direct3d-11-devices-8464b8d294.md)
</dt> </dl>