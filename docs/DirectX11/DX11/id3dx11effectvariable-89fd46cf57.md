Source: [https://learn.microsoft.com/en-us/windows/win32/direct3d11/id3dx11effectvariable](<https://learn.microsoft.com/en-us/windows/win32/direct3d11/id3dx11effectvariable>)

# ID3DX11EffectVariable interface

The **ID3DX11EffectVariable** interface is the base class for all effect variables.

The lifetime of an **ID3DX11EffectVariable** object is equal to the lifetime of its parent [**ID3DX11Effect**](./id3dx11effect-277b450b03.md) object.

-   [Methods](#methods)

### Methods

The **ID3DX11EffectVariable** interface has these methods.



| Method                                                                           | Description                                            |
|:---------------------------------------------------------------------------------|:-------------------------------------------------------|
| [**AsBlend**](./id3dx11effectvariable-asblend-e519d0e405.md)                                 | Get a effect-blend variable.<br/>                |
| [**AsClassInstance**](./id3dx11effectvariable-asclassinstance-048663ba3b.md)                 | Get a class-instance variable.<br/>              |
| [**AsConstantBuffer**](./id3dx11effectvariable-asconstantbuffer-941d4c15ab.md)               | Get a constant buffer.<br/>                      |
| [**AsDepthStencil**](./id3dx11effectvariable-asdepthstencil-4b868d659a.md)                   | Get a depth-stencil variable.<br/>               |
| [**AsDepthStencilView**](./id3dx11effectvariable-asdepthstencilview-eed284069b.md)           | Get a depth-stencil-view variable.<br/>          |
| [**AsInterface**](./id3dx11effectvariable-asinterface-a5c7bd4640.md)                         | Get an interface variable.<br/>                  |
| [**AsMatrix**](./id3dx11effectvariable-asmatrix-c95b3d9e4a.md)                               | Get a matrix variable.<br/>                      |
| [**AsRasterizer**](./id3dx11effectvariable-asrasterizer-8fe6806c87.md)                       | Get a rasterizer variable.<br/>                  |
| [**AsRenderTargetView**](./id3dx11effectvariable-asrendertargetview-494a558353.md)           | Get a render-target-view variable.<br/>          |
| [**AsSampler**](./id3dx11effectvariable-assampler-534b6a5d23.md)                             | Get a sampler variable.<br/>                     |
| [**AsScalar**](./id3dx11effectvariable-asscalar-a26b75ef76.md)                               | Get a scalar variable.<br/>                      |
| [**AsShader**](./id3dx11effectvariable-asshader-13d847da2b.md)                               | Get a shader variable.<br/>                      |
| [**AsShaderResource**](./id3dx11effectvariable-asshaderresource-cae34608bd.md)               | Get a shader-resource variable.<br/>             |
| [**AsString**](./id3dx11effectvariable-asstring-95be85cd27.md)                               | Get a string variable.<br/>                      |
| [**AsUnorderedAccessView**](./id3dx11effectvariable-asunorderedaccessview-dfa9c37b1e.md)     | Get an unordered-access-view variable.<br/>      |
| [**AsVector**](./id3dx11effectvariable-asvector-90f6813050.md)                               | Get a vector variable.<br/>                      |
| [**GetAnnotationByIndex**](./id3dx11effectvariable-getannotationbyindex-c820e89024.md)       | Get an annotation by index.<br/>                 |
| [**GetAnnotationByName**](./id3dx11effectvariable-getannotationbyname-67ed0a9893.md)         | Get an annotation by name.<br/>                  |
| [**GetDesc**](./id3dx11effectvariable-getdesc-83e2e00120.md)                                 | Get a description.<br/>                          |
| [**GetElement**](./id3dx11effectvariable-getelement-44cd343463.md)                           | Get an array element.<br/>                       |
| [**GetMemberByIndex**](./id3dx11effectvariable-getmemberbyindex-d8fc52097d.md)               | Get a structure member by index.<br/>            |
| [**GetMemberByName**](./id3dx11effectvariable-getmemberbyname-39abe1dbdb.md)                 | Get a structure member by name.<br/>             |
| [**GetMemberBySemantic**](./id3dx11effectvariable-getmemberbysemantic-52e69e5263.md)         | Get a structure member by semantic.<br/>         |
| [**GetParentConstantBuffer**](./id3dx11effectvariable-getparentconstantbuffer-7ab102530e.md) | Get a constant buffer.<br/>                      |
| [**GetRawValue**](./id3dx11effectvariable-getrawvalue-bdb610cf61.md)                         | Get data.<br/>                                   |
| [**GetType**](./id3dx11effectvariable-gettype-9801c6e6a1.md)                                 | Get type information.<br/>                       |
| [**IsValid**](./id3dx11effectvariable-isvalid-c0ad788b13.md)                                 | Compare the data type with the data stored.<br/> |
| [**SetRawValue**](./id3dx11effectvariable-setrawvalue-ae81ec3bf4.md)                         | Set data.<br/>                                   |



 

## Remarks

> [!Note]  
> The DirectX SDK does not supply any compiled binaries for effects. You must use Effects 11 source to build your effects-type application. For more information about using Effects 11 source, see [Differences Between Effects 10 and Effects 11](./d3d11-graphics-programming-guide-effects-differences-f7025c8c69.md).

 

## Requirements



| Requirement | Value |
|--------------------|----------------------------------------------------------------------------------------------------------------------------------------------|
| Header<br/>  | <dl> <dt>D3dx11effect.h</dt> </dl>                                                    |
| Library<br/> | <dl> <dt>N/A (An Effects 11 library is available online as shared source.)</dt> </dl> |



## See also

<dl> <dt>

[Effects 11 Interfaces](./d3d11-graphics-reference-effects11-interfaces-5b7b91a9df.md)
</dt> <dt>

[D3DX Interfaces](./d3d11-graphics-reference-d3dx11-interfaces-bf8653ed03.md)
</dt> </dl>