Source: [https://learn.microsoft.com/en-us/windows/win32/direct3d11/direct3d-11-advanced-stages-domain-shader-create](<https://learn.microsoft.com/en-us/windows/win32/direct3d11/direct3d-11-advanced-stages-domain-shader-create>)

# How To: Create a Domain Shader

A domain shader is the third of three stages that work together to implement [tessellation](./direct3d-11-advanced-stages-tessellation-1063a02933.md). The inputs for the domain-shader stage come from a hull shader. This topic shows how to create a domain shader.

A domain shader transforms surface geometry (created by the fixed-function tessellator stage) using hull shader output-control points, hull shader output patch-constant data, and a single set of tessellator uv coordinates.

**To create a domain shader**

1.  Design a domain shader. See [How To: Design a Domain Shader](./direct3d-11-advanced-stages-domain-shader-design-5cc5c1d78f.md).
2.  Compile the shader code.
3.  Create a domain-shader object using [**ID3D11Device::CreateDomainShader**](./nf-d3d11-id3d11device-createdomainshader-c5636e5eef.md).
    ```
    HRESULT CreateDomainShader(
      const void *pShaderBytecode, // 
      SIZE_T BytecodeLength, // 
      ID3D11ClassLinkage *pClassLinkage, // 
      ID3D11DomainShader **ppDomainShader
    );
    ```

    

4.  Initialize the pipeline stage using [**ID3D11DeviceContext::DSSetShader**](./nf-d3d11-id3d11devicecontext-dssetshader-2714e40815.md).
    ```
    void DSSetShader(
      ID3D11DomainShader *pDomainShader, // 
      ID3D11ClassInstance *const *ppClassInstances,
      UINT NumClassInstances
    );
    ```

    

A domain shader must be bound to the pipeline if a hull shader is bound. In particular, it is not valid to directly stream out hull shader control points with the geometry shader.

## Related topics

<dl> <dt>

[How to Use Direct3D 11](./how-to-use-direct3d-11-112ea0ccbf.md)
</dt> <dt>

[Tessellation Overview](./direct3d-11-advanced-stages-tessellation-1063a02933.md)
</dt> </dl>