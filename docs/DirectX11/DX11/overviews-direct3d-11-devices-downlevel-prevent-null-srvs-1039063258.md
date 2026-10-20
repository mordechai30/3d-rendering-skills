Source: [https://learn.microsoft.com/en-us/windows/win32/direct3d11/overviews-direct3d-11-devices-downlevel-prevent-null-srvs](<https://learn.microsoft.com/en-us/windows/win32/direct3d11/overviews-direct3d-11-devices-downlevel-prevent-null-srvs>)

# Preventing Unwanted NULL Pixel Shader SRVs

Direct3D 11 applications that run on Direct3D 9 graphics hardware could inadvertently cause the driver to receive **NULL** shader-resource views (SRVs) even when the applications bind non-**NULL** SRVs to the pixel shader stage. This situation can occur only if the applications destroy SRVs while they execute. This topic discusses how to work around the driver receiving **NULL** shader-resource views (SRVs) even when non-**NULL** SRVs are bound to the pixel shader stage.

To prevent the driver from receiving unwanted **NULL** SRVs, the applications must call [**ID3D11DeviceContext::PSSetShaderResources**](./nf-d3d11-id3d11devicecontext-pssetshaderresources-b29b7757c2.md) to unset all SRVs before each call to [**ID3D11DeviceContext::PSSetShader**](./nf-d3d11-id3d11devicecontext-pssetshader-830ddd515f.md). However, if the applications do not destroy SRVs until the end of their code execution, they do not need to unset the SRVs.

The [10Level9 Reference](./d3d11-graphics-reference-10level9-71856f59bf.md) section lists the differences between how various [**ID3D11Device**](./nn-d3d11-id3d11device-6e49ef4b9e.md) and [**ID3D11DeviceContext**](./nn-d3d11-id3d11devicecontext-abe911f651.md) methods behave at various 10Level9 feature levels.

## Related topics

<dl> <dt>

[Direct3D 11 on Downlevel Hardware](./overviews-direct3d-11-devices-downlevel-366ef41a88.md)
</dt> </dl>