Source: [https://learn.microsoft.com/en-us/windows/win32/api/D3D11Shader/nn-d3d11shader-id3d11moduleinstance](<https://learn.microsoft.com/en-us/windows/win32/api/D3D11Shader/nn-d3d11shader-id3d11moduleinstance>)

# ID3D11ModuleInstance interface


## -description

A module-instance interface is used for resource rebinding. <div class="alert"><b>Note</b>  This interface is part of the HLSL shader linking technology that you can use on all Direct3D 11 platforms to create precompiled HLSL functions, package them into libraries, and link them into full shaders at run time.
          </div>
<div> </div>

## -inheritance

The <b>ID3D11ModuleInstance</b> interface inherits from the <a href="/windows/desktop/api/unknwn/nn-unknwn-iunknown">IUnknown</a> interface. <b>ID3D11ModuleInstance</b> also has these types of members:

## -remarks

To get a module-instance interface, call <a href="/windows/desktop/api/d3d11shader/nf-d3d11shader-id3d11module-createinstance">ID3D11Module::CreateInstance</a> or <a href="/windows/desktop/api/d3d11shader/nf-d3d11shader-id3d11functionlinkinggraph-createmoduleinstance">ID3D11FunctionLinkingGraph::CreateModuleInstance</a>.
      

<div class="alert"><b>Note</b>  <b>ID3D11ModuleInstance</b> requires the D3dcompiler_47.dll or a later version of the DLL.
      </div>
<div> </div>

## -see-also

<a href="/windows/desktop/api/unknwn/nn-unknwn-iunknown">IUnknown</a>



<a href="/windows/desktop/direct3d11/d3d11-graphics-reference-d3d11-shader-interfaces">Shader Interfaces</a>