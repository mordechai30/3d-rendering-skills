Source: [https://learn.microsoft.com/en-us/windows/win32/api/D3D11Shader/nn-d3d11shader-id3d11linkingnode](<https://learn.microsoft.com/en-us/windows/win32/api/D3D11Shader/nn-d3d11shader-id3d11linkingnode>)

# ID3D11LinkingNode interface


## -description

A linking-node interface is used for shader linking. <div class="alert"><b>Note</b>  This interface is part of the HLSL shader linking technology that you can use on all Direct3D 11 platforms to create precompiled HLSL functions, package them into libraries, and link them into full shaders at run time.
          </div>
<div> </div>

## -remarks

To get a linking-node interface, call <a href="/windows/desktop/api/d3d11shader/nf-d3d11shader-id3d11functionlinkinggraph-setinputsignature">ID3D11FunctionLinkingGraph::SetInputSignature</a>, <a href="/windows/desktop/api/d3d11shader/nf-d3d11shader-id3d11functionlinkinggraph-setoutputsignature">ID3D11FunctionLinkingGraph::SetOutputSignature</a>, or <a href="/windows/desktop/api/d3d11shader/nf-d3d11shader-id3d11functionlinkinggraph-callfunction">ID3D11FunctionLinkingGraph::CallFunction</a>.
      

<div class="alert"><b>Note</b>  <b>ID3D11LinkingNode</b> requires the D3dcompiler_47.dll or a later version of the DLL.
      </div>
<div> </div>

## -see-also

<a href="/windows/desktop/api/unknwn/nn-unknwn-iunknown">IUnknown</a>



<a href="/windows/desktop/direct3d11/d3d11-graphics-reference-d3d11-shader-interfaces">Shader Interfaces</a>