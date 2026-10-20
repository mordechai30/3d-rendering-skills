Source: [https://learn.microsoft.com/en-us/windows/win32/api/D3D11Shader/nn-d3d11shader-id3d11shaderreflection](<https://learn.microsoft.com/en-us/windows/win32/api/D3D11Shader/nn-d3d11shader-id3d11shaderreflection>)

# ID3D11ShaderReflection interface


## -description

A shader-reflection interface accesses shader information.

## -inheritance

The <b>ID3D11ShaderReflection</b> interface inherits from the <a href="/windows/desktop/api/unknwn/nn-unknwn-iunknown">IUnknown</a> interface. <b>ID3D11ShaderReflection</b> also has these types of members:

## -remarks

An <b>ID3D11ShaderReflection</b> interface can be retrieved for a shader by using  <a href="/windows/desktop/direct3dhlsl/d3dreflect">D3DReflect</a>.  The following code illustrates retrieving a <b>ID3D11ShaderReflection</b>  from a shader.
          


```
pd3dDevice->CreatePixelShader( pPixelShaderBuffer->GetBufferPointer(),
                               pPixelShaderBuffer->GetBufferSize(), g_pPSClassLinkage, &g_pPixelShader );

ID3D11ShaderReflection* pReflector = NULL; 
D3DReflect( pPixelShaderBuffer->GetBufferPointer(), pPixelShaderBuffer->GetBufferSize(), 
            IID_ID3D11ShaderReflection, (void**) &pReflector);
```

## -see-also

<a href="/windows/desktop/api/unknwn/nn-unknwn-iunknown">IUnknown</a>



<a href="/windows/desktop/direct3d11/d3d11-graphics-reference-d3d11-shader-interfaces">Shader Interfaces</a>