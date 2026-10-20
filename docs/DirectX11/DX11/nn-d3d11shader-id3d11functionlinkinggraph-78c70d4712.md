Source: [https://learn.microsoft.com/en-us/windows/win32/api/D3D11Shader/nn-d3d11shader-id3d11functionlinkinggraph](<https://learn.microsoft.com/en-us/windows/win32/api/D3D11Shader/nn-d3d11shader-id3d11functionlinkinggraph>)

# ID3D11FunctionLinkingGraph interface


## -description

A function-linking-graph interface is used for constructing shaders that consist of a sequence of precompiled function calls that pass values to each other. <div class="alert"><b>Note</b>  This interface is part of the HLSL shader linking technology that you can use on all Direct3D 11 platforms to create precompiled HLSL functions, package them into libraries, and link them into full shaders at run time.
</div>
<div> </div>

## -inheritance

The <b>ID3D11FunctionLinkingGraph</b> interface inherits from the <a href="/windows/desktop/api/unknwn/nn-unknwn-iunknown">IUnknown</a> interface. <b>ID3D11FunctionLinkingGraph</b> also has these types of members:

## -remarks

To get a function-linking-graph interface, call <a href="/windows/desktop/api/d3dcompiler/nf-d3dcompiler-d3dcreatefunctionlinkinggraph">D3DCreateFunctionLinkingGraph</a>. 

You can use the function-linking-graph (FLG) interface methods to construct shaders that consist of a sequence of precompiled function calls that pass values to each other. You don't need to write HLSL and then call the HLSL compiler. Instead, the shader structure is specified programmatically via a C++ API. FLG nodes represent input and output signatures and invocations of precompiled library functions. The order of registering the function-call nodes defines the sequence of invocations. You must specify the input signature node first and the output signature node last. FLG edges define how values are passed from one node to another. The data types of passed values must be the same; there is no implicit type conversion. Shape and swizzling rules follow the HLSL behavior. Values can only be passed forward in this sequence.

<div class="alert"><b>Note</b>  <b>ID3D11FunctionLinkingGraph</b> requires the D3dcompiler_47.dll or a later version of the DLL. </div>
<div> </div>

## -see-also

<a href="/windows/desktop/api/unknwn/nn-unknwn-iunknown">IUnknown</a>



<a href="/windows/desktop/direct3d11/d3d11-graphics-reference-d3d11-shader-interfaces">Shader Interfaces</a>