Source: [https://learn.microsoft.com/en-us/windows/win32/direct3d11/direct3d-11-advanced-stages-tessellator-initialize](<https://learn.microsoft.com/en-us/windows/win32/direct3d11/direct3d-11-advanced-stages-tessellator-initialize>)

# How To: Initialize the Tessellator Stage

In general, tessellation expands the compact, user-defined, model of a patch into geometry that contains a programmable amount of detail. The geometry is typically a set of triangles that represents detailed surface geometry. This topic shows how to initialize the tessellator stage.

The tessellator stage is the second of three stages that work together to tessellate or tile a surface. The first stage is the hull-shader stage; it operates once per patch and configures how the next stage (the fixed function tessellator) behaves. A hull shader also generates user-defined outputs such as output-control points and patch constants that are sent past the tessellator directly to the third stage, the domain-shader stage. A domain shader is invoked once per tessellator-stage point and evaluates surface positions.

The tessellator stage is a fixed function stage, there is no shader to generate, and no state to set. It receives all of its setup state from the hull-shader stage; once the hull-shader stage has been initialized, the tessellator stage is automatically initialized.

**To initialize the tessellator stage**

-   Initialize the hull-shader stage using [**ID3D11DeviceContext::HSSetShader**](./nf-d3d11-id3d11devicecontext-hssetshader-adf112d8b0.md).

    ```
    void HSSetShader(
      ID3D11HullShader *pHullShader,  
      ID3D11ClassInstance *const *ppClassInstances,
      UINT NumClassInstances
    );
    ```

    

    *ppClassInstances* is a pointer to an array of shader interfaces, represented by [**ID3D11ClassInstance**](./nn-d3d11-id3d11classinstance-60b20918e7.md) pointers and the number of interfaces, represented by *NumClassInstances*. If not used, these parameters can be set to **NULL** and 0 respectively.

After the hull-shader stage is initialized, you should also initialize the domain-shader stage.

## Related topics

<dl> <dt>

[How to Use Direct3D 11](./how-to-use-direct3d-11-112ea0ccbf.md)
</dt> <dt>

[Tessellation Overview](./direct3d-11-advanced-stages-tessellation-1063a02933.md)
</dt> </dl>