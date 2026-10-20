Source: [https://learn.microsoft.com/en-us/windows/win32/direct3d11/d3d11-graphics-programming-guide-effects-interfaces](<https://learn.microsoft.com/en-us/windows/win32/direct3d11/d3d11-graphics-programming-guide-effects-interfaces>)

# Effect System Interfaces (Direct3D 11)

The effect system defines several interfaces for managing effect state. There are two types of interfaces: those used by the runtime to render an effect and reflection interfaces for getting and setting effect variables.

-   [Effect Runtime Interfaces](#effect-runtime-interfaces)
-   [Effect Reflection Interfaces](#effect-reflection-interfaces)

## Effect Runtime Interfaces

Use runtime interfaces to render an effect.



| Runtime Interfaces                                       | Description                                                    |
|----------------------------------------------------------|----------------------------------------------------------------|
| [**ID3DX11Effect**](./id3dx11effect-277b450b03.md)                   | Collection of one or more groups and techniques for rendering. |
| [**ID3DX11EffectPass**](./id3dx11effectpass-6c2d5d6dfa.md)           | A collection of state assignments.                             |
| [**ID3DX11EffectTechnique**](./id3dx11effecttechnique-b79e863e91.md) | A collection of one or more passes.                            |
| [**ID3DX11EffectGroup**](./id3dx11effectgroup-2a6f9fee4c.md)         | A collection of one or more techniques.                        |



 

## Effect Reflection Interfaces

Reflection is implemented in the effect system to support reading (and writing) effect state. There are multiple ways to access effect variables.

### Setting Groups of Effect State

Use these interfaces to get and set a group of state.



| Reflection Interfaces                                                          | Description                      |
|--------------------------------------------------------------------------------|----------------------------------|
| [**ID3DX11EffectBlendVariable**](./id3dx11effectblendvariable-1cac3f92ff.md)               | Get and set blend state.         |
| [**ID3DX11EffectDepthStencilVariable**](./id3dx11effectdepthstencilvariable-a77c0fc1c1.md) | Get and set depth-stencil state. |
| [**ID3DX11EffectRasterizerVariable**](./id3dx11effectrasterizervariable-134fac5726.md)     | Get and set rasterizer state.    |
| [**ID3DX11EffectSamplerVariable**](./id3dx11effectsamplervariable-7ff68716ca.md)           | Get and set sampler state.       |



 

### Setting Effect Resources

Use these interfaces to get and set resources.



| Reflection Interfaces                                                                        | Description                                         |
|----------------------------------------------------------------------------------------------|-----------------------------------------------------|
| [**ID3DX11EffectConstantBuffer**](./id3dx11effectconstantbuffer-ee6cbea9bf.md)                           | Access data in a texture buffer or constant buffer. |
| [**ID3DX11EffectDepthStencilViewVariable**](./id3dx11effectdepthstencilviewvariable-0b6e536a0c.md)       | Access data in a depth-stencil resource.            |
| [**ID3DX11EffectRenderTargetViewVariable**](./id3dx11effectrendertargetviewvariable-44dbfb8cd0.md)       | Access data in a render target.                     |
| [**ID3DX11EffectShaderResourceVariable**](./id3dx11effectshaderresourcevariable-d5157ae671.md)           | Access data in a shader resource.                   |
| [**ID3DX11EffectUnorderedAccessViewVariable**](./id3dx11effectunorderedaccessviewvariable-af8945de78.md) | Access data in an unordered access view.            |



 

### Setting Other Effect Variables

Use these interfaces to get and set state by the variable type.



| Reflection Interfaces                                                            | Description               |
|----------------------------------------------------------------------------------|---------------------------|
| [**ID3DX11EffectClassInstanceVariable**](./id3dx11effectclassinstancevariable-7764ee39f2.md) | Get a class instance.     |
| [**ID3DX11EffectInterfaceVariable**](./id3dx11effectinterfacevariable-ee6aee853e.md)         | Get and set an interface. |
| [**ID3DX11EffectMatrixVariable**](./id3dx11effectmatrixvariable-2bcd48d5b8.md)               | Get and set a matrix.     |
| [**ID3DX11EffectScalarVariable**](./id3dx11effectscalarvariable-74af8e3b01.md)               | Get and set a scalar.     |
| [**ID3DX11EffectShaderVariable**](./id3dx11effectshadervariable-81ab8d90dd.md)               | Get a shader variable.    |
| [**ID3DX11EffectStringVariable**](./id3dx11effectstringvariable-0a2d7dee98.md)               | Get and set a string.     |
| [**ID3DX11EffectType**](./id3dx11effecttype-fd26b9b277.md)                                   | Get a variable type.      |
| [**ID3DX11EffectVectorVariable**](./id3dx11effectvectorvariable-5517295c3c.md)               | Get and set a vector.     |



 

All reflection interfaces derive from [**ID3DX11EffectVariable**](./id3dx11effectvariable-89fd46cf57.md).

## Related topics

<dl> <dt>

[Effects (Direct3D 11)](./d3d11-graphics-programming-guide-effects-16146534b6.md)
</dt> <dt>

[Programming Guide for Direct3D 11](./dx-graphics-overviews-1c65710e07.md)
</dt> </dl>