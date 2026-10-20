Source: [https://learn.microsoft.com/en-us/windows/win32/api/D3D11/nn-d3d11-id3d11classlinkage](<https://learn.microsoft.com/en-us/windows/win32/api/D3D11/nn-d3d11-id3d11classlinkage>)

# ID3D11ClassLinkage interface


## -description

This interface encapsulates an HLSL dynamic linkage.

## -inheritance

The <b>ID3D11ClassLinkage</b> interface inherits from <a href="/windows/desktop/api/d3d11/nn-d3d11-id3d11devicechild">ID3D11DeviceChild</a>. <b>ID3D11ClassLinkage</b> also has these types of members:

## -remarks

A class linkage object can hold up to 64K gotten instances. A gotten instance is a handle that references a variable name in any shader that is created with that linkage object. When you create a shader with a class linkage object, the runtime gathers these instances and stores them in the class linkage object. For more information about how a class linkage object is used, see <a href="/windows/desktop/direct3dhlsl/storing-variables-and-types-for-shaders-to-share">Storing Variables and Types for Shaders to Share</a>.

An <b>ID3D11ClassLinkage</b> object is created using the <a href="/windows/desktop/api/d3d11/nf-d3d11-id3d11device-createclasslinkage">ID3D11Device::CreateClassLinkage</a> method.

## -see-also

<a href="/windows/desktop/direct3d11/d3d11-graphics-reference-d3d11-core-interfaces">Core Interfaces</a>



<a href="/windows/desktop/api/d3d11/nn-d3d11-id3d11devicechild">ID3D11DeviceChild</a>



<a href="/windows/desktop/direct3d11/d3d11-graphics-reference-d3d11-shader-interfaces">Shader Interfaces</a>