Source: [https://walbourn.github.io/living-without-d3dx/](<https://walbourn.github.io/living-without-d3dx/>)

[Home](https://walbourn.github.io/) | [Posts by Tag](https://walbourn.github.io/tags/) | [Posts by Month](https://walbourn.github.io/archive/)  
  


<a id="living-without-d3dx"></a>

# Living without D3DX

 direct3d, dxsdk  
  
Originally posted to Chuck Walbourn's Blog on MSDN, Aug 20, 2013


---

Over the past few years, I’ve been working on a number of projects in part motivated by the need to replace legacy D3DX functionality. As noted on [Microsoft Docs](https://docs.microsoft.com/en-us/windows/desktop/directx-sdk--august-2009-), all versions of D3DX are deprecated and are not shipped with the Windows 8.x SDK. This includes D3DX9, D3DX10, and D3DX11. There are plenty of options for moving existing code over to newer, more supportable solutions most of which are now shared-source.

I’ve built a number of porting notes tables for each of these topics, and then realized today I don’t have a single place to see it all. So here it is, the “D3DX porting mega-table” for Direct3D 11.

> There is an option for obtaining the deprecated D3DX9, D3DX10, and/or D3DX11 libraries without using the legacy DirectX SDK or redist via [NuGet](https://www.nuget.org/packages/Microsoft.DXSDK.D3DX). The open source replacements listed below are still preferable. See [this blog post](https://walbourn.github.io/legacy-d3dx-on-nuget/) for more details.

**Direct3D 9:** There are limited replacements for the functionality in D3DX9 if you are still using Direct3D 9. You can make use of D3DCompile APIs directly with the legacy DirectX SDK, but newer versions of the D3DCompile DLL in the Windows 8.x SDK are not compatible with Windows XP for runtime use. You can use DirectXMath for Direct3D 9 instead of D3DXMath or XNAMath via [NuGet](https://www.nuget.org/packages/directxmath). You can find Direct3D 9 versions of DDSTextureLoader, WICTextureLoader, and ScreenGrab on [GitHub](https://github.com/microsoft/DirectXTex/). You can use [DirectXTex](https://walbourn.github.io/directxtex/) and [DirectXMesh](https://walbourn.github.io/directxmesh/) when preparing content for use by Direct3D 9 (the [texconv](https://github.com/microsoft/DirectXTex/wiki/Texconv) tool supports a `-dx9` switch for this purpose).

**Direct3D 10:** The best option for Direct3D 10.x applications is to update them to use Direct3D 11, and then utilize all the options here to replace legacy D3XD10. Porting the API is very [straightforward](https://docs.microsoft.com/en-us/windows/desktop/direct3d11/d3d11-programming-guide-migrating), and Direct3D 11 is [available](https://docs.microsoft.com/en-us/windows/desktop/direct3darticles/direct3d11-deployment) on all supported platforms that have Direct3D 10.

**Direct3D 12:** There is a header that ships in the DirectX 12 samples on [GitHub](https://github.com/microsoft/DirectX-Headers/blob/main/include/directx/d3dx12.h) called `d3dx12.h`. It is all inline utility header which has no DLL or redistributable dependency, and can be used under the MIT license. It is not included in the Windows SDK. If you are looking for additional functionality, see the [DirectX Tool Kit for DirectX 12](https://walbourn.github.io/directx-tool-kit-for-directx-12/), [DirectXTex and DirectXMesh](https://walbourn.github.io/directxtex-and-directxmesh-now-support-direct3d-12/).

**Related:** [Where is the DirectX SDK?](https://aka.ms/dxsdk), [DirectX SDKs of a certain age](https://walbourn.github.io/directx-sdks-of-a-certain-age/), [DXUT for Win32 Desktop Update](https://walbourn.github.io/dxut-for-win32-desktop-update/), [DirectX SDK Samples Catalog](https://walbourn.github.io/directx-sdk-samples-catalog/), [DirectX SDK Tools Catalog](https://walbourn.github.io/directx-sdk-tools-catalog/)

**CodePlex:**All CodePlex links will redirect to the Microsoft organizational section of GitHub as CodePlex has been [shutdown](https://devblogs.microsoft.com/bharry/shutting-down-codeplex).

<a id="general-helpers"></a>

# General Helpers

The [DirectX Tool Kit](https://walbourn.github.io/directxtk/) provides a number of helpers that are designed to simplify Direct3D 11 programming in the tradition of the original D3DX library. You can find the library on [GitHub](https://github.com/Microsoft/DirectXTK).

|  |  |
| --- | --- |
| `ID3DX10Sprite` | `SpriteBatch` |
| `ID3DX10Font` | `SpriteFont SpriteBatch` |
| `ID3DX10Mesh` | `Model ModelMesh ModelMeshPart ModelBone` |
| `D3DXCreateBox  D3DXCreateCylinder  D3DXCreateSphere  D3DXCreateTeapot  D3DXCreateTorus` | `GeometricPrimitive` |
| `D3DXCreatePolygon` | `PrimitiveBatch` |
| `D3DX11CreateShaderResourceViewFromFile` | `CreateXXXTextureFromFile` |
| `D3DX11CreateShaderResourceViewFromResource  D3DX11CreateShaderResourceViewFromMemory` | `CreateXXXTextureFromMemory` |
| `D3DX11CreateTextureFromFile` | `CreateXXXTextureFromFile` |
| `D3DX11CreateTextureFromResource  D3DX11CreateTextureFromMemory` | `CreateXXXTextureFromMemory` |
| `D3DX11SaveTextureToFile` | `SaveXXXTextureToFile` |

The DXERR library is another helper that shipped in the legacy DirectX SDK. In Windows 8.x or later, you can just use `FormatMessage` to use the built-in error descriptions which support DirectX. Otherwise, the best replacement is to compile your own version of DXERR.

|  |  |
| --- | --- |
| `DXGetErrorString DXGetErrorDescription DXTrace` | See [Where's DXERR.LIB?](https://walbourn.github.io/wheres-dxerr-lib/) |

<a id="hlsl-functions"></a>

# HLSL Functions

The HLSL compiler, shader reflection API, and related functionality has been broken out into it’s own [D3DCompile](https://walbourn.github.io/hlsl-fxc-and-d3dcompile/) DLL for some time. D3DCompile is in the Windows 8.x SDK and is included with VS 2012 and VS 2013 Preview.

|  |  |
| --- | --- |
| `D3DXCompileShaderFromFile  D3DX10CompileFromFile  D3DX11CompileFromFile` | [D3DCompileFromFile](https://docs.microsoft.com/en-us/windows/desktop/api/d3dcompiler/nf-d3dcompiler-d3dcompilefromfile) |
| `D3DXCompileShader  D3D10CompileShader  D3DX10CompileFromMemory  D3DX11CompileFromMemory` | [D3DCompile](https://docs.microsoft.com/en-us/windows/desktop/api/d3dcompiler/nf-d3dcompiler-d3dcompile) |
| `D3DXCompileShaderFromResource  D3DX10CompileFromResource  D3DX11CompileFromResource` | No direct equivalent. Can use resource APIs and then `D3DCompile` above. |
| `D3DXPreprocessShader  D3DXPreprocessShaderFromFile  D3DXPreprocessShaderFromResource  D3D10PreprocessShader  D3DX10PreprocessShaderFromFile  D3DX10PreprocessShaderFromMemory  D3DX10PreprocessShaderFromResource  D3DX11PreprocessShaderFromFile  D3DX11PreprocessShaderFromMemory  D3DX11PreprocessShaderFromResource` | [D3DPreprocess](https://docs.microsoft.com/en-us/windows/desktop/api/d3dcompiler/nf-d3dcompiler-d3dpreprocess) |
| `D3DXDisassembleShader  D3D10DisassembleShader  D3DX10DisassembleShader` | [D3DDisassemble](https://docs.microsoft.com/en-us/windows/desktop/api/d3dcompiler/nf-d3dcompiler-d3ddisassemble) |
| `D3D10ReflectShader  D3DX10ReflectShader` | [D3DReflect](https://docs.microsoft.com/en-us/windows/desktop/api/d3dcompiler/nf-d3dcompiler-d3dreflect) [D3D11Reflect](https://docs.microsoft.com/en-us/windows/desktop/direct3dhlsl/d3d11reflect) |
| `ID3DXBuffer  ID3D10Blob` | [ID3DBlob](http://msdn.microsoft.com/en-us/library/windows/desktop/ff728743.aspx) |
| `D3DXCreateBuffer  D3D10CreateBlob` | [D3DCreateBlob](https://docs.microsoft.com/en-us/windows/desktop/api/d3dcompiler/nf-d3dcompilerd3dcreateblob) |
| `D3D10GetInputSignatureBlob  D3D10GetOutputSignatureBlob  D3D10GetInputAndOutputSignatureBlob  D3D10GetShaderDebugInfo` | [D3DGetBlobPart](https://docs.microsoft.com/en-us/windows/desktop/api/d3dcompiler/nf-d3dcompiler-d3dgetblobpart) |

<a id="texture-functions"></a>

# Texture Functions

The [DirectXTex](https://walbourn.github.io/directxtex/) library is primarily intended for [texture processing](https://walbourn.github.io/direct3d-11-textures-and-block-compression/) offline with tools, although it can also be used at runtime for doing texture block compression, mipmap generation, or handling more general image processing needs. [DirectXTK](https://walbourn.github.io/directxtk/) is intended for use at runtime with light-weight helpers and image loaders, but does not provide support for general runtime texture format conversion. You can find both libraries on [GitHub](https://github.com/Microsoft/DirectXTex).

|  |  |
| --- | --- |
| `D3DX11ComputeNormalMap` | DirectXTex library,  `ComputeNormalMap` |
| `D3DX11CreateShaderResourceViewFromFile D3DX11CreateTextureFromFile` | DDSTextureLoader: `CreateDDSTextureFromFile` WICTextureLoader: `CreateWICTextureFromFile` DirectXTex library (tools), `LoadFromXXXFile` then `CreateShaderResourceView` or `CreateTexture` |
| `D3DX11CreateShaderResourceViewFromMemory D3DX11CreateTextureFromMemory` | DDSTextureLoader: `CreateDDSTextureFromMemory` WICTextureLoader: `CreateWICTextureFromMemory` DirectXTex library (tools), `LoadFromXXXMemory` then `CreateShaderResourceView` or `CreateTexture` |
| `D3DX11CreateShaderResourceViewFromResource D3DX11CreateTextureFromResource` | No direct equivalent, can use Win32 resource functions and then the 'from memory' APIs above. |
| `D3DX11FilterTexture` | DirectXTex library, `GenerateMipMaps` and `GenerateMipMaps3D` |
| `D3DX11GetImageInfoFromFile` | DirectXTex library, `GetMetadataFromXXXFile` |
| `D3DX11GetImageInfoFromMemory` | DirectXTex library, `GetMetadataFromXXXMemory` |
| `D3DX11GetImageInfoFromResource` | No direct equivalent, can use Win32 resource functions and then the 'from memory' APIs above. |
| `D3DX11LoadTextureFromTexture` | DirectXTex library, `Resize`, `Convert`, `Compress`, `Decompress`, and/or `CopyRectangle` |
| `D3DX11SaveTextureToFile` | ScreenGrab: `SaveDDSTextureToFile` or `SaveWICTextureToFile` DirectXTex library, `CaptureTexture` then `SaveToXXXFile` |
| `D3DX11SaveTextureToMemory` | DirectXTex library, `CaptureTexture` then `SaveToXXXMemory` |

<a id="geometry-functions"></a>

# Geometry Functions

The [DirectXMesh](https://walbourn.github.io/directxmesh/) library is intended for geometry processing offline with tools, although it can be used at runtime. You can find the library on [GitHub](https://github.com/Microsoft/DirectXMesh).

|  |  |
| --- | --- |
| `D3DXCleanMesh` | `Clean` |
| `D3DXComputeNormals` | `ComputeNormals` |
| `D3DXComputeTangent  D3DXComputeTangentFrame  D3DXComputeTangentFrameEx` | `ComputeTangentFrame` |
| `ID3DX10Mesh::GenerateAdjacencyAndPointReps` | `GenerateAdjacencyAndPointReps` |
| `ID3DX10Mesh::GenerateGSAdjacency` | `GenerateGSAdjacency` |
| `ID3DX10Mesh::Optimize` | `AttributeSort OptimizeFacesEx OptimizeVertices ReorderIB FinalizeIB FinalizeVB` |
| `D3DXOptimizeFaces` | `OptimizeFaces` |
| `D3DXOptimizeVertices` | `OptimizeVertices` |
| `D3DXValidMesh` | `Validate` |
| `D3DXWeldVertices` | `WeldVertices CompactVB` |
| `D3DXGetFVFVertexSize  D3DXGetDeclVertexSize  D3DXGetDeclLength  D3DXDeclaratorFromFVF  D3DXFVFFromDeclarator` | `FlexibleVertexFormat.h` |

<a id="math"></a>

# Math

The legacy D3DXMath library has been replaced by [DirectXMath](https://walbourn.github.io/introducing-directxmath/). The library is in the Windows 8.x SDK or later, as well as being available on [GitHub](https://github.com/Microsoft/DirectXMath). You may also want to take a look at the [SimpleMath](SimpleMath.md) wrapper.

|  |  |
| --- | --- |
| `D3DXFLOAT16` | `HALF` |
| `D3DXMATRIXA16` | `XMMATRIX` or `XMFLOAT4X4A` |
| `D3DXMATRIX` | `XMFLOAT4X4` |
| `D3DXQUATERNION` `D3DXPLANE` `D3DXCOLOR` | `XMVECTOR` is used rather than having unique types, so you will likely need to use an `XMFLOAT4` |
| `D3DXVECTOR2` | `XMFLOAT2` |
| `D3DXVECTOR2_16F` | `XMHALF2` |
| `D3DXVECTOR3` | `XMFLOAT3` |
| `D3DXVECTOR4` | `XMFLOAT4` (or if you can guarantee the data is 16-byte aligned, `XMVECTOR` or `XMFLOAT4A`) |
| `D3DXVECTOR4_16F` | `XMHALF4` |
| `D3DX_PI` | `XM_PI` |
| `D3DX_1BYPI` | `XM_1DIVPI` |
| `D3DXToRadian` | `XMConvertToRadians` |
| `D3DXToDegree` | `XMConvertToDegrees` |
| `D3DXBoxBoundProbe` | `BoundingBox::Intersects(XMVECTOR, XMVECTOR, float&)` |
| `D3DXComputeBoundingBox` | `BoundingBox::CreateFromPoints` |
| `D3DXComputeBoundingSphere` | `BoundingSphere::CreateFromPoints` |
| `D3DXSphereBoundProbe` | `BoundingSphere::Intersects(XMVECTOR, XMVECTOR, float&)` |
| `D3DXIntersectTriFunction` | `TriangleTests::Intersects` |
| `D3DXFloat32To16Array` | `XMConvertFloatToHalfStream` |
| `D3DXFloat16To32Array` | `XMConvertHalfToFloatStream` |
| `D3DXVec2Length` | `XMVector2LengthEst` |
| `D3DXVec2LengthSq` | `XMVector2LengthSq` |
| `D3DXVec2Dot` | `XMVector2Dot` |
| `D3DXVec2CCW` | `XMVector2Cross` |
| `D3DXVec2Add` | `XMVectorAdd` |
| `D3DXVec2Subtract` | `XMVectorSubtract` |
| `D3DXVec2Minimize` | `XMVectorMin` |
| `D3DXVec2Maximize` | `XMVectorMax` |
| `D3DXVec2Scale` | `XMVectorScale` |
| `D3DXVec2Lerp` | `XMVectorLerpV` |
| `D3DXVec2Normalize` | `XMVector2NormalizeEst` |
| `D3DXVec2Hermite` | `XMVectorHermiteV` |
| `D3DXVec2CatmullRom` | `XMVectorCatmullRomV` |
| `D3DXVec2BaryCentric` | `XMVectorBaryCentricV` |
| `D3DXVec2Transform` | `XMVector2Transform` |
| `D3DXVec2TransformCoord` | `XMVector2TransformCoord` |
| `D3DXVec2TransformNormal` | `XMVector2TransformNormal` |
| `D3DXVec2TransformArray` | `XMVector2TransformStream` |
| `D3DXVec2TransformCoordArray` | `XMVector2TransformCoordStream` |
| `D3DXVec2TransformNormalArray` | `XMVector2TransformNormalStream` |
| `D3DXVec3Length` | `XMVector3LengthEst` |
| `D3DXVec3LengthSq` | `XMVector3LengthSq` |
| `D3DXVec3Dot` | `XMVector3Dot` |
| `D3DXVec3Cross` | `XMVector3Cross` |
| `D3DXVec3Add` | `XMVectorAdd` |
| `D3DXVec3Subtract` | `XMVectorSubtract` |
| `D3DXVec3Minimize` | `XMVectorMin` |
| `D3DXVec3Maximize` | `XMVectorMax` |
| `D3DXVec3Scale` | `XMVectorScale` |
| `D3DXVec3Lerp` | `XMVectorLerpV` |
| `D3DXVec3Normalize` | `XMVector3NormalizeEst` |
| `D3DXVec3Hermite` | `XMVectorHermiteV` |
| `D3DXVec3CatmullRom` | `XMVectorCatmullRomV` |
| `D3DXVec3BaryCentric` | `XMVectorBaryCentricV` |
| `D3DXVec3Transform` | `XMVector3Transform` |
| `D3DXVec3TransformCoord` | `XMVector3TransformCoord` |
| `D3DXVec3TransformNormal` | `XMVector3TransformNormal` |
| `D3DXVec3TransformArray` | `XMVector3TransformStream` |
| `D3DXVec3TransformCoordArray` | `XMVector3TransformCoordStream` |
| `D3DXVec3TransformNormalArray` | `XMVector3TransformNormalStream` |
| `D3DXVec3Project` | `XMVector3Project` |
| `D3DXVec3Unproject` | `XMVector3Unproject` |
| `D3DXVec3ProjectArray` | `XMVector3ProjectStream` |
| `D3DXVec3UnprojectArray` | `XMVector3UnprojectStream` |
| `D3DXVec4Length` | `XMVector4LengthEst` |
| `D3DXVec4LengthSq` | `XMVector4LengthSq` |
| `D3DXVec4Dot` | `XMVector4Dot` |
| `D3DXVec4Add` | `XMVectorAdd` |
| `D3DXVec4Subtract` | `XMVectorSubtract` |
| `D3DXVec4Minimize` | `XMVectorMin` |
| `D3DXVec4Maximize` | `XMVectorMax` |
| `D3DXVec4Scale` | `XMVectorScale` |
| `D3DXVec4Lerp` | `XMVectorLerpV` |
| `D3DXVec4Cross` | `XMVector4Cross` |
| `D3DXVec4Normalize` | `XMVector4NormalizeEst` |
| `D3DXVec4Hermite` | `XMVectorHermiteV` |
| `D3DXVec4CatmullRom` | `XMVectorCatmullRomV` |
| `D3DXVec4BaryCentric` | `XMVectorBaryCentricV` |
| `D3DXVec4Transform` | `XMVector4Transform` |
| `D3DXVec4TransformArray` | `XMVector4TransformStream` |
| `D3DXMatrixIdentity` | `XMMatrixIdentity` |
| `D3DXMatrixDeterminant` | `XMMatrixDeterminant` |
| `D3DXMatrixDecompose` | `XMMatrixDecompose` |
| `D3DXMatrixTranspose` | `XMMatrixTranspose` |
| `D3DXMatrixMultiply` | `XMMatrixMultiply` |
| `D3DXMatrixMultiplyTranspose` | `XMMatrixMultiplyTranspose` |
| `D3DXMatrixInverse` | `XMMatrixInverse` |
| `D3DXMatrixScaling` | `XMMatrixScaling` |
| `D3DXMatrixTranslation` | `XMMatrixTranslation` |
| `D3DXMatrixRotationX` | `XMMatrixRotationX` |
| `D3DXMatrixRotationY` | `XMMatrixRotationY` |
| `D3DXMatrixRotationZ` | `XMMatrixRotationZ` |
| `D3DXMatrixRotationAxis` | `XMMatrixRotationAxis` |
| `D3DXMatrixRotationQuaternion` | `XMMatrixRotationQuaternion` |
| `D3DXMatrixRotationYawPitchRoll` | `XMMatrixRotationRollPitchYaw` (Note the order of parameters is different: D3DXMath takes yaw, pitch, roll, DirectXMath takes pitch, yaw, roll) |
| `D3DXMatrixTransformation` | `XMMatrixTransformation` |
| `D3DXMatrixTransformation2D` | `XMMatrixTransformation2D` |
| `D3DXMatrixAffineTransformation` | `XMMatrixAffineTransformation` |
| `D3DXMatrixAffineTransformation2D` | `XMMatrixAffineTransformation2D` |
| `D3DXMatrixLookAtRH` | `XMMatrixLookAtRH` |
| `D3DXMatrixLookAtLH` | `XMMatrixLookAtLH` |
| `D3DXMatrixPerspectiveRH` | `XMMatrixPerspectiveRH` |
| `D3DXMatrixPerspectiveLH` | `XMMatrixPerspectiveLH` |
| `D3DXMatrixPerspectiveFovRH` | `XMMatrixPerspectiveFovRH` |
| `D3DXMatrixPerspectiveFovLH` | `XMMatrixPerspectiveFovLH` |
| `D3DXMatrixPerspectiveOffCenterRH` | `XMMatrixPerspectiveOffCenterRH` |
| `D3DXMatrixPerspectiveOffCenterLH` | `XMMatrixPerspectiveOffCenterLH` |
| `D3DXMatrixOrthoRH` | `XMMatrixOrthographicRH` |
| `D3DXMatrixOrthoLH` | `XMMatrixOrthographicLH` |
| `D3DXMatrixOrthoOffCenterRH` | `XMMatrixOrthographicOffCenterRH` |
| `D3DXMatrixOrthoOffCenterLH` | `XMMatrixOrthographicOffCenterLH` |
| `D3DXMatrixShadow` | `XMMatrixShadow` |
| `D3DXMatrixReflect` | `XMMatrixReflect` |
| `D3DXQuaternionLength` | `XMQuaternionLength` |
| `D3DXQuaternionLengthSq` | `XMQuaternionLengthSq` |
| `D3DXQuaternionDot` | `XMQuaternionDot` |
| `D3DXQuaternionIdentity` | `XMQuaternionIdentity` |
| `D3DXQuaternionIsIdentity` | `XMQuaternionIsIdentity` |
| `D3DXQuaternionConjugate` | `XMQuaternionConjugate` |
| `D3DXQuaternionToAxisAngle` | `XMQuaternionToAxisAngle` |
| `D3DXQuaternionRotationMatrix` | `XMQuaternionRotationMatrix` |
| `D3DXQuaternionRotationAxis` | `XMQuaternionRotationAxis` |
| `D3DXQuaternionRotationYawPitchRoll` | `XMQuaternionRotationRollPitchYaw` (Note the order of parameters is different: D3DXMath takes yaw, pitch, roll, DirectXMath takes pitch, yaw, roll) |
| `D3DXQuaternionMultiply` | `XMQuaternionMultiply` |
| `D3DXQuaternionNormalize` | `XMQuaternionNormalizeEst` |
| `D3DXQuaternionInverse` | `XMQuaternionInverse` |
| `D3DXQuaternionLn` | `XMQuaternionLn` |
| `D3DXQuaternionExp` | `XMQuaternionExp` |
| `D3DXQuaternionSlerp` | `XMQuaternionSlerpV` |
| `D3DXQuaternionSquad` | `XMQuaternionSquadV` |
| `D3DXQuaternionSquadSetup` | `XMQuaternionSquadSetup` |
| `D3DXQuaternionBaryCentric` | `XMQuaternionBaryCentricV` |
| `D3DXPlaneDot` | `XMPlaneDot` |
| `D3DXPlaneDotCoord` | `XMPlaneDotCoord` |
| `D3DXPlaneDotNormal` | `XMPlaneDotNormal` |
| `D3DXPlaneScale` | `XMVectorScale` |
| `D3DXPlaneNormalize` | `XMPlaneNormalizeEst` |
| `D3DXPlaneIntersectLine` | `XMPlaneIntersectLine` |
| `D3DXPlaneFromPointNormal` | `XMPlaneFromPointNormal` |
| `D3DXPlaneFromPoints` | `XMPlaneFromPoints` |
| `D3DXPlaneTransform` | `XMPlaneTransform` |
| `D3DXPlaneTransformArray` | `XMPlaneTransformStream` |
| `D3DXColorNegative` | `XMColorNegative` |
| `D3DXColorAdd` | `XMVectorAdd` |
| `D3DXColorSubtract` | `XMVectorSubtract` |
| `D3DXColorScale` | `XMVectorScale` |
| `D3DXColorModulate` | `XMColorModulate` |
| `D3DXColorLerp` | `XMVectorLerpV` |
| `D3DXColorAdjustSaturation` | `XMColorAdjustSaturation` |
| `D3DXColorAdjustContrast` | `XMColorAdjustContrast` |
| `D3DXFresnelTerm` | `XMFresnelTerm` |

<a id="spherical-harmonics-math"></a>

# Spherical Harmonics Math

The [SHmath](https://walbourn.github.io/spherical-harmonics-math/) library is available as an add-on for DirectXMath.

|  |  |
| --- | --- |
| `XMSHEvalDirection` | Evaluates the Spherical Harmonic basis functions. Equivalent to [D3DXSHEvalDirection](https://docs.microsoft.com/en-us/windows/desktop/direct3d9/d3dxshevaldirection) function. |
| `XMSHRotate` | Rotates SH vector by a rotation matrix. Equivalent to the <a href="https://docs.microsoft.com/en-us/windows/desktop/direct3d10/d3d10-d3dxshrotate>D3DXSHRotate</a> function. |
| `XMSHRotateZ` | Rotates the SH vector in the Z axis by an angle. Equivalent to the [D3DXSHRotateZ](https://docs.microsoft.com/en-us/windows/desktop/direct3d9/d3dxshrotatez) function. |
| `XMSHAdd` | Adds two SH vectors. Equivalent to the <a href="https://docs.microsoft.com/en-us/windows/desktop/direct3d9/d3dxshadd>D3DXSHAdd</a> function. |
| `XMSHScale` | Scales a SH vector. Equivalent to the [D3DXSHScale](https://docs.microsoft.com/en-us/windows/desktop/direct3d10/d3d10-d3dxshscale) function. |
| `XMSHDot` | Computes the dot product of two SH vectors. Equivalent to the [D3DXSHDot](https://docs.microsoft.com/en-us/windows/desktop/direct3d9/d3dxshdot) function. |
| `XMSHMultiply  XMSHMultiply2  XMSHMultiply3  XMSHMultiply4  XMSHMultiply5  XMSHMultiply6` | Computes the product of two functions represented using SH. Equivalent to [D3DXSHMultiply2](https://docs.microsoft.com/en-us/windows/desktop/direct3d9/d3dxshmultiply2), `D3DXSHMultiply3`, `D3DXSHMultiply4`, `D3DXSHMultiply5`, and `D3DXSHMultiply6`. |
| `XMSHEvalDirectionalLight` | Evaluates a directional light and returns spectral SH data. Equivalent to the [D3DXSHEvalDirectionalLight](https://docs.microsoft.com/en-us/windows/desktop/direct3d10/d3d10-d3dxshevaldirectionallight) function. |
| `XMSHEvalSphericalLight` | Evaluates a spherical light and returns spectral SH data. Equivalent to the [D3DXEvalSphericalLight](https://docs.microsoft.com/en-us/windows/desktop/direct3d9/d3dxshevalsphericallight) function. |
| `XMSHEvalConeLight` | Evaluates a light that is a cone of constant intensity and returns spectral SH data. Equivalent to the [D3DXSHEvalConeLight](https://docs.microsoft.com/en-us/windows/desktop/direct3d10/d3d10-d3dxshevalconelight) function. |
| `XMSHEvalHemisphereLight` | Evaluates a light that is a linear interpolant between two colors over the sphere. Equivalent to the [D3DXSHEvalHemisphereLight](https://docs.microsoft.com/en-us/windows/desktop/direct3d10/d3d10-d3dxshevalhemispherelight) function. |
| `SHProjectCubeMap` | Projects a function represented in a cube map into spherical harmonics. Equivalent to the [D3DX11SHProjectCubeMap](https://docs.microsoft.com/en-us/windows/desktop/direct3d11/d3dx11shprojectcubemap) function. |

<a id="math-matrix-stack"></a>

# Math Matrix Stack

A DirectXMath-based version of `D3DXCreateMatrixStack` / `ID3DXMATRIXStack` is available on the [DirectXMath](https://github.com/microsoft/DirectXMath/blob/main/MatrixStack/DirectXMatrixStack.h) GitHub.

<a id="effects-fx"></a>

# Effects (FX)

The [Effects system for Direct3D 11](https://walbourn.github.io/effects-for-direct3d-11-update/) is primarily provided as a porting aid for older code. The library is available on [GitHub](https://github.com/Microsoft/FX11).

|  |  |
| --- | --- |
| `D3DXCreateEffect  D3DXCreateEffectEx  D3DXCreateEffectFromResource  D3DXCreateEffectFromResourceEx  D3D10CompileEffectFromMemory` | `D3DX11CompileEffectFromMemory` |
| `D3DXCreateEffectFromFile  D3DXCreateEffectFromFileEx` | `D3DX11CompileEffectFromFile` |
| `D3D10CreateEffectFromMemory` | `D3DX11CreateEffectFromMemory` |
| `D3DXCreateEffectPool  D3D10CreateEffectPoolFromMemory` | Effects 11 does not support 'effect pools' or `D3DCOMPILE_EFFECT_CHILD_EFFECT`. Effect [groups](https://docs.microsoft.com/en-us/windows/desktop/direct3d11/d3d11-effect-group-syntax) provide a more efficient solution for common scenarios previously addressed with 'effect pools' |
| `D3DXDisassembleEffect  D3D10DisassembleEffect` | `D3DDisassemble` `D3DDisassemble10Effect` in D3DCompile |

<a id="performanceprofiling"></a>

# Performance/Profiling

D3DX9 included the entry-points intercepted by PIX for Windows for performance profiling. This is now handled by the DirectX runtime directly and is monitored by the Visual Studio Graphics Diagnostics tool.

|  |  |
| --- | --- |
| `D3DPERF_BeginEvent  D3DPERF_EndEvent  D3DPERF_SetMarker  D3DPERF_SetRegion  D3DPERF_QueryRepeatFrame  D3DPERF_SetOptions  D3DPERF_GetStatus` | [ID3DUserDefinedAnnotation](https://docs.microsoft.com/en-us/windows/desktop/api/d3d11_1/nn-d3d11_1-id3duserdefinedannotation) which is supported by the DirectX 11.1 runtime on Windows 8.x and Windows 7 Service Pack 1 + [KB2670838](https://walbourn.github.io/directx-11-1-and-windows-7-update/)    If using DirectX 11.2+, you can use [ID3D11DeviceContext2](https://docs.microsoft.com/en-us/windows/desktop/api/d3d11_2/nn-d3d11_2-id3d11devicecontext2) directly for BeginEventInt, SetMarkerInt, and EndEvent.    For DirectX12, use the [WinPixEventRuntime](https://devblogs.microsoft.com/pix/winpixeventruntime/) NuGet package. |

<a id="uvatlas-functions"></a>

# UVAtlas Functions

The [UVAtlas](https://walbourn.github.io/uvatlas-return-of-the-isochart/) library is intended for isochart creation offline with tools, although it can be used at runtime. You can find the library on [GitHub](https://github.com/Microsoft/UVAtlas).

|  |  |
| --- | --- |
| `D3DXUVAtlasCreate` | `UVAtlasCreate` |
| `D3DXUVAtlasPartition` | `UVAtlasPartition` |
| `D3DXUVAtlasPack` | `UVAtlasPack` |
| `D3DXComputeIMTFromPerVertexSignal` | `UVAtlasComputeIMTFromPerVertexSignal` |
| `D3DXComputeIMTFromPerTexelSignal` | `UVAtlasComputeIMTFromPerTexelSignal` |
| `D3DXComputeIMTFromSignal` | `UVAtlasComputeIMTFromSignal` |
| `D3DXComputeIMTFromTexture` | `UVAtlasComputeIMTFromTexture` |

<a id="xfile-io"></a>

# XFile I/O

The DirectX® X-File format was dropped for Direct3D 10+, so if you need processing for these files the recommendation is to make use of the [Microsoft.DXSDK.D3DX](https://walbourn.github.io/legacy-d3dx-on-nuget/) NuGet package and the associated [D3DX XFile](https://learn.microsoft.com/windows/win32/direct3d9/dx9-graphics-reference-d3dx-x-file) APIs such as `ID3DXFile` which are hosted in the `D3DX9_43.DLL`.

> Avoid using the ‘inbox’ [legacy X-File APIs](https://learn.microsoft.com/windows/win32/direct3d9/dx9-graphics-reference-x-file) such as `IDirectXFile`. Use of the D3DX9 version is much preferred for forward compatibilty. This older version is also x86 (32-bit) only.

<a id="miscellaneous"></a>

# Miscellaneous

|  |  |
| --- | --- |
| D3DX9Anim | See the animation utility code for *DirectX Tool Kit* for [DX11](Using-skinned-models.md) / [DX12](https://github.com/microsoft/DirectXTK12/wiki/Using-skinned-models).</tr> </tr> |
| `ID3DXRenderToSurface` | See the `RenderTexture` utility for [DX11](RenderTexture.md) / [DX12](https://github.com/microsoft/DirectXTK12/wiki/RenderTexture). |
| `ID3DXLine` | Use of [Direct2D](https://learn.microsoft.com/windows/win32/direct2d/direct2d-portal) either directly or via interop is the recommended solution for styled-lines and other "presentation" graphics rendering. </tbody> </table>  <a id="note"></a>  NoteCareful readers will note that there are a few omissions from this table. Use the [NuGet package](https://www.nuget.org/packages/Microsoft.DXSDK.D3DX) if you still need this functionality.  - The Precomputed Radiance Transfer (PRT) simulator is only available in closed-source form in legacy D3DX9. There are a number of papers that cover this technology in the literature, and the most generally useful parts of this functionality are the [SHmath](https://walbourn.github.io/spherical-harmonics-math/) functions which are available. - Progressive Mesh (P-Mesh) is only available in closed-source form in legacy D3DX9.  <a id="background"></a>  BackgroundA few folks have asked why the D3DX libraries were deprecated in the first place in the transition to the Windows 8.x SDK. D3DX has been a useful set of utility code for Direct3D applications since Direct3D 7, but has a presented a number of challenges over the years. The primary one is that as a 'closed-source' utility library; it was difficult to debug, resolve performance issues, or apply hot-fixes without taking a dependency on a newer release of the DirectX SDK. Second, with the security requirements that came with the adoption of the [Secure Development Lifecycle](https://www.microsoft.com/en-us/securityengineering/sdl/) (SDL) at Microsoft, the transition to a DLL rather than a static library created a redistribution requirement that  [complicated setup](https://walbourn.github.io/not-so-direct-setup/) for many developers--note that static libraries have their own problems such as being specific to a particular release of the compiler including service pack level. D3DX9 itself became a bit bloated which resulted in a DLL larger than many EXEs that used it. Finally, the actual usable content of subsequent generations of D3DX left D3DX11 with not much in it. The need for useful utility code is still there, but it is now being solved with various 'shared-source' solutions rather than a monolithic closed-source DLL like D3DX. |
