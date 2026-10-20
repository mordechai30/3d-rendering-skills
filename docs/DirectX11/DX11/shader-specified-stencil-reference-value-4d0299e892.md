Source: [https://learn.microsoft.com/en-us/windows/win32/direct3d11/shader-specified-stencil-reference-value](<https://learn.microsoft.com/en-us/windows/win32/direct3d11/shader-specified-stencil-reference-value>)

# Shader Specified Stencil Reference Value (Direct3D 11 Graphics)

Enabling pixel shaders to output the Stencil Reference Value, rather than using the API-specified one, enables a very fine granular control over stencil operations.

The shader specified value replaces the API-specified *Stencil Reference Value* for that invocation, which means the change affects both the stencil test, and when stencil op D3D11\_STENCIL\_OP\_REPLACE (one member of [**D3D11\_STENCIL\_OP**](./ne-d3d11-d3d11_stencil_op-58054597b6.md)) is used to write the reference value to the stencil buffer.

In earlier versions of D3D11, the Stencil Reference Value can only be specified by the [**ID3D11DeviceContext::OMSetDepthStencilState**](./nf-d3d11-id3d11devicecontext-omsetdepthstencilstate-23de8be94b.md) method. This means that this value can only be defined on a per-draw granularity. This D3D11.3 feature enables developers to read and use the Stencil Reference Value (`SV_StencilRef`) that is output from a pixel shader, meaning that it can be specified on a per-pixel or per-sample granularity.

This feature is optional in D3D11.3. To test for its support, check the `PSSpecifiedStencilRefSupported` boolean field of [**D3D11\_FEATURE\_DATA\_D3D11\_OPTIONS2**](./ns-d3d11-d3d11_feature_data_d3d11_options2-c4464cbb03.md) using [**ID3D11Device::CheckFeatureSupport**](./nf-d3d11-id3d11device-checkfeaturesupport-ec5826ac8e.md)

Here is an example of the use of `SV_StencilRef` in a pixel shader:

``` syntax
uint main2(float4 c : COORD) : SV_StencilRef
{
    return uint(c.x);
}
```

## Related topics

<dl> <dt>

[Direct3D 11.3 Features](./direct3d-11-3-features-87cd0e6b8b.md)
</dt> <dt>

[Shader Model 5.1](/windows/desktop/direct3dhlsl/shader-model-5-1)
</dt> </dl>