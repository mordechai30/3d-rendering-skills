Source: [https://learn.microsoft.com/en-us/windows/win32/direct3d11/d3d11-graphics-reference-d3d11-shader-interfaces](<https://learn.microsoft.com/en-us/windows/win32/direct3d11/d3d11-graphics-reference-d3d11-shader-interfaces>)

# Shader Interfaces (Direct3D 11 Graphics)

This section contains information about the shader interfaces.

Each of these shader interfaces manages a compiled shader. The interface is created when a shader is compiled, and is then passed to various APIs that need access to a compiled shader; such as when binding a shader to a pipeline stage or getting a shader signature.


## In this section




| Topic | Description | 
|-------|-------------|
| <a href="/windows/desktop/api/D3D11/nn-d3d11-id3d11classinstance"><strong>ID3D11ClassInstance</strong></a><br /> | This interface encapsulates an HLSL class.<br /> | 
| <a href="/windows/desktop/api/D3D11/nn-d3d11-id3d11classlinkage"><strong>ID3D11ClassLinkage</strong></a><br /> | This interface encapsulates an HLSL dynamic linkage.<br /> | 
| <a href="/windows/desktop/api/d3d11/nn-d3d11-id3d11computeshader"><strong>ID3D11ComputeShader</strong></a><br /> | A compute-shader interface manages an executable program (a compute shader) that controls the compute-shader stage.<br /> | 
| <a href="/windows/desktop/api/d3d11/nn-d3d11-id3d11domainshader"><strong>ID3D11DomainShader</strong></a><br /> | A domain-shader interface manages an executable program (a domain shader) that controls the domain-shader stage.<br /> | 
| [**ID3D11FunctionLinkingGraph**](./nn-d3d11shader-id3d11functionlinkinggraph-78c70d4712.md)<br> | A function-linking-graph interface is used for constructing shaders that consist of a sequence of precompiled function calls that pass values to each other. <br> **Note:** This interface is part of the HLSL shader linking technology that you can use on all Direct3D 11 platforms to create precompiled HLSL functions, package them into libraries, and link them into full shaders at run time.<br> | 
| [**ID3D11FunctionReflection**](./nn-d3d11shader-id3d11functionreflection-7d77d2a341.md)<br> | A function-reflection interface accesses function info. <br> **Note:** This interface is part of the HLSL shader linking technology that you can use on all Direct3D 11 platforms to create precompiled HLSL functions, package them into libraries, and link them into full shaders at run time.<br> | 
| [**ID3D11FunctionParameterReflection**](./nn-d3d11shader-id3d11functionparameterreflection-5154092d2d.md)<br> | A function-parameter-reflection interface accesses function-parameter info. <br> **Note:** This interface is part of the HLSL shader linking technology that you can use on all Direct3D 11 platforms to create precompiled HLSL functions, package them into libraries, and link them into full shaders at run time.<br> | 
| <a href="/windows/desktop/api/d3d11/nn-d3d11-id3d11geometryshader"><strong>ID3D11GeometryShader</strong></a><br /> | A geometry-shader interface manages an executable program (a geometry shader) that controls the geometry-shader stage.<br /> | 
| <a href="/windows/desktop/api/d3d11/nn-d3d11-id3d11hullshader"><strong>ID3D11HullShader</strong></a><br /> | A hull-shader interface manages an executable program (a hull shader) that controls the hull-shader stage.<br /> | 
| [**ID3D11LibraryReflection**](./nn-d3d11shader-id3d11libraryreflection-e108a6bdef.md)<br> | A library-reflection interface accesses library info. <br> **Note:** This interface is part of the HLSL shader linking technology that you can use on all Direct3D 11 platforms to create precompiled HLSL functions, package them into libraries, and link them into full shaders at run time.<br> | 
| [**ID3D11Linker**](./nn-d3d11shader-id3d11linker-e266086291.md)<br> | A linker interface is used to link a shader module. <br> **Note:** This interface is part of the HLSL shader linking technology that you can use on all Direct3D 11 platforms to create precompiled HLSL functions, package them into libraries, and link them into full shaders at run time.<br> | 
| [**ID3D11LinkingNode**](./nn-d3d11shader-id3d11linkingnode-8db786478d.md)<br> | A linking-node interface is used for shader linking. <br> **Note:** This interface is part of the HLSL shader linking technology that you can use on all Direct3D 11 platforms to create precompiled HLSL functions, package them into libraries, and link them into full shaders at run time.<br> | 
| [**ID3D11Module**](./nn-d3d11shader-id3d11module-bb418f4c7d.md)<br> | A module interface creates an instance of a module that is used for resource rebinding. <br> **Note:** This interface is part of the HLSL shader linking technology that you can use on all Direct3D 11 platforms to create precompiled HLSL functions, package them into libraries, and link them into full shaders at run time.<br> | 
| [**ID3D11ModuleInstance**](./nn-d3d11shader-id3d11moduleinstance-3f6f260066.md)<br> | A module-instance interface is used for resource rebinding. <br> **Note:** This interface is part of the HLSL shader linking technology that you can use on all Direct3D 11 platforms to create precompiled HLSL functions, package them into libraries, and link them into full shaders at run time.<br> | 
| <a href="/windows/desktop/api/d3d11/nn-d3d11-id3d11pixelshader"><strong>ID3D11PixelShader</strong></a><br /> | A pixel-shader interface manages an executable program (a pixel shader) that controls the pixel-shader stage.<br /> | 
| <a href="/windows/desktop/api/D3D11Shader/nn-d3d11shader-id3d11shaderreflection"><strong>ID3D11ShaderReflection</strong></a><br /> | A shader-reflection interface accesses shader information.<br /> | 
| <a href="/windows/desktop/api/D3D11Shader/nn-d3d11shader-id3d11shaderreflectionconstantbuffer"><strong>ID3D11ShaderReflectionConstantBuffer</strong></a><br /> | This shader-reflection interface provides access to a constant buffer.<br /> | 
| <a href="/windows/desktop/api/D3D11Shader/nn-d3d11shader-id3d11shaderreflectiontype"><strong>ID3D11ShaderReflectionType</strong></a><br /> | This shader-reflection interface provides access to variable type.<br /> | 
| <a href="/windows/desktop/api/D3D11Shader/nn-d3d11shader-id3d11shaderreflectionvariable"><strong>ID3D11ShaderReflectionVariable</strong></a><br /> | This shader-reflection interface provides access to a variable.<br /> | 
| <a href="/windows/desktop/api/D3D11ShaderTracing/nn-d3d11shadertracing-id3d11shadertrace"><strong>ID3D11ShaderTrace</strong></a><br /> | An <a href="/windows/desktop/api/D3D11ShaderTracing/nn-d3d11shadertracing-id3d11shadertrace"><strong>ID3D11ShaderTrace</strong></a> interface implements methods for obtaining traces of shader executions.<br /> | 
| <a href="/windows/desktop/api/D3D11ShaderTracing/nn-d3d11shadertracing-id3d11shadertracefactory"><strong>ID3D11ShaderTraceFactory</strong></a><br /> | An <a href="/windows/desktop/api/D3D11ShaderTracing/nn-d3d11shadertracing-id3d11shadertracefactory"><strong>ID3D11ShaderTraceFactory</strong></a> interface implements a method for generating shader trace information objects.<br /> | 
| <a href="/windows/desktop/api/d3d11/nn-d3d11-id3d11vertexshader"><strong>ID3D11VertexShader</strong></a><br /> | A vertex-shader interface manages an executable program (a vertex shader) that controls the vertex-shader stage.<br /> | 




 

## Related topics

<dl> <dt>

[Shader Reference](./d3d11-graphics-reference-d3d11-shader-35d5334ee4.md)
</dt> </dl>