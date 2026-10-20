Source: [https://learn.microsoft.com/en-us/windows/win32/direct3d11/d3d11-effect-states](<https://learn.microsoft.com/en-us/windows/win32/direct3d11/d3d11-effect-states>)

# Effect State Groups (Direct3D 11)

Effect states are name value pairs in the form of an expression.

-   [Blend State](#blend-state)
-   [Depth and Stencil State](#depth-and-stencil-state)
-   [Rasterizer State](#rasterizer-state)
-   [Sampler State](#sampler-state)
-   [Effect Object State](#effect-object-state)
-   [Defining and using state objects](#defining-and-using-state-objects)
-   [Related topics](#related-topics)

## Blend State



| Effect state                                                                                                                      | Group                                                          |
|-----------------------------------------------------------------------------------------------------------------------|-----------------------------------------------------------|
| ALPHATOCOVERAGEENABLEBLENDENABLESRCBLENDDESTBLENDBLENDOP SRCBLENDALPHADESTBLENDALPHABLENDOPALPHARENDERTARGETWRITEMASK | Members of [**D3D11\_BLEND\_DESC**](./ns-d3d11-d3d11_blend_desc-dbb11ca57b.md) |



 

## Depth and Stencil State



|  Effect state                                                                                                                                                              | Group                                                                              |
|----------------------------------------------------------------------------------------------------------------------------------------------------------------|-------------------------------------------------------------------------------|
| DEPTHENABLEDEPTHWRITEMASKDEPTHFUNCSTENCILENABLESTENCILREADMASKSTENCILWRITEMASK                                                                                 | Members of [**D3D11\_DEPTH\_STENCIL\_DESC**](./ns-d3d11-d3d11_depth_stencil_desc-e5f1b30def.md)    |
| FRONTFACESTENCILFAILFRONTFACESTENCILZFAILFRONTFACESTENCILPASSFRONTFACESTENCILFUNCBACKFACESTENCILFAILBACKFACESTENCILZFAILBACKFACESTENCILPASSBACKFACESTENCILFUNC | Member of [**D3D11\_DEPTH\_STENCILOP\_DESC**](./ns-d3d11-d3d11_depth_stencilop_desc-2fd3546157.md) |



 

## Rasterizer State



| Effect state                                                                                                                                | Group                                                                    |
|---------------------------------------------------------------------------------------------------------------------------------|---------------------------------------------------------------------|
| FILLMODE                                                                                                                        | [**D3D11\_FILL\_MODE**](./ne-d3d11-d3d11_fill_mode-7e29592dfd.md)                        |
| CULLMODE                                                                                                                        | [**D3D11\_CULL\_MODE**](./ne-d3d11-d3d11_cull_mode-b74f74f5d7.md)                        |
| FRONTCOUNTERCLOCKWISEDEPTHBIASDEPTHBIASCLAMPSLOPESCALEDDEPTHBIAS ZCLIPENABLESCISSORENABLEMULTISAMPLEENABLEANTIALIASEDLINEENABLE | Members of [**D3D11\_RASTERIZER\_DESC**](./ns-d3d11-d3d11_rasterizer_desc-e92b0458ca.md) |



 

## Sampler State



| Effect state                                                                                                    | Group                                                              |
|-----------------------------------------------------------------------------------------------------|---------------------------------------------------------------|
| Filter AddressU AddressV AddressW MipLODBias MaxAnisotropy ComparisonFunc BorderColor MinLOD MaxLOD | Members of [**D3D11\_SAMPLER\_DESC**](./ns-d3d11-d3d11_sampler_desc-f05d3e5368.md) |



 

See [Sampler Type (DirectX HLSL)](/windows/desktop/direct3dhlsl/dx-graphics-hlsl-sampler) for examples.

## Effect Object State



| This Effect Object                          | Maps to                                                             |
|---------------------------------------------|---------------------------------------------------------------------|
| RASTERIZERSTATE                             | A [Rasterizer State](#rasterizer-state) state object.               |
| DEPTHSTENCILSTATE                           | A [Depth and Stencil State](#depth-and-stencil-state) state object. |
| BLENDSTATE                                  | A [Blend State](#blend-state) state object.                         |
| VERTEXSHADER                                | A compiled vertex shader object.                                    |
| PIXELSHADER                                 | A compiled pixel shader object.                                     |
| GEOMETRYSHADER                              | A compiled geometry shader object.                                  |
| DS\_STENCILREFAB\_BLENDFACTORAB\_SAMPLEMASK | Members of [**D3DX11\_PASS\_DESC**](./d3dx11-pass-desc-b5cf3b922b.md).          |



 

## Defining and using state objects

State objects are declared in FX files in the following format. StateObjectType is one of the states listed above and MemberName is the name of any member that will have a non-default value.


```
StateObjectType ObjectName {
  MemberName = value;
  ...
  MemberName = value;
};
    
```



For example, to set up a blend state object with AlphaToCoverageEnable and BlendEnable\[0\] set to **FALSE** the following code would be used.


```
BlendState NoBlend {
  AlphaToCoverageEnable = FALSE;
  BlendEnable[0] = FALSE;
};
    
```



The state object is applied to a technique pass using one of the SetStateGroup functions described in [Effect Technique Syntax (Direct3D 11)](./d3d11-effect-technique-syntax-dc7ec0dae9.md). For example, to apply the BlendState object described above the following code would be used.


```
SetBlendState( NoBlend, float4( 0.0f, 0.0f, 0.0f, 0.0f ), 0xFFFFFFFF );
    
```



## Related topics

<dl> <dt>

[Effect Technique Syntax](./d3d11-effect-technique-syntax-dc7ec0dae9.md)
</dt> <dt>

[Effect Format (Direct3D 11)](./d3d11-effect-format-a65df79688.md)
</dt> </dl>