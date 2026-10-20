Source: [https://learn.microsoft.com/en-us/windows/win32/api/D3D11Shader/nn-d3d11shader-id3d11functionreflection](<https://learn.microsoft.com/en-us/windows/win32/api/D3D11Shader/nn-d3d11shader-id3d11functionreflection>)

# ID3D11FunctionReflection interface


## -description

A function-reflection interface accesses function info. <div class="alert"><b>Note</b>  This interface is part of the HLSL shader linking technology that you can use on all Direct3D 11 platforms to create precompiled HLSL functions, package them into libraries, and link them into full shaders at run time.
</div>
<div> </div>

## -inheritance

The <b>ID3D11FunctionReflection</b> interface inherits from the <a href="/windows/desktop/api/unknwn/nn-unknwn-iunknown">IUnknown</a> interface. <b>ID3D11FunctionReflection</b> also has these types of members:
<ul>
<li><a href="/">Methods</a></li>
</ul>

## -remarks

To get a function-reflection interface, call <a href="/windows/desktop/api/d3d11shader/nf-d3d11shader-id3d11libraryreflection-getfunctionbyindex">ID3D11LibraryReflection::GetFunctionByIndex</a>. This isn't a COM interface, so you don't need to worry about reference counts or releasing the interface when you're done with it.

<div class="alert"><b>Note</b>  <b>ID3D11FunctionReflection</b> requires the D3dcompiler_47.dll or a later version of the DLL. </div>
<div> </div>

## -see-also

<a href="/windows/desktop/direct3d11/d3d11-graphics-reference-d3d11-shader-interfaces">Shader Interfaces</a>