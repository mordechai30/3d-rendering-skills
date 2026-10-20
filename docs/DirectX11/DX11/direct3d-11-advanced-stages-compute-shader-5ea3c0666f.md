Source: [https://learn.microsoft.com/en-us/windows/win32/direct3d11/direct3d-11-advanced-stages-compute-shader](<https://learn.microsoft.com/en-us/windows/win32/direct3d11/direct3d-11-advanced-stages-compute-shader>)

# Compute Shader Overview

A compute shader is a programmable shader stage that expands Microsoft Direct3D 11 beyond graphics programming. The compute shader technology is also known as the DirectCompute technology.

Like other programmable shaders (vertex and geometry shaders for example), a compute shader is designed and implemented with [HLSL](/windows/desktop/direct3dhlsl/dx-graphics-hlsl) but that is just about where the similarity ends. A compute shader provides high-speed general purpose computing and takes advantage of the large numbers of parallel processors on the graphics processing unit (GPU). The compute shader provides memory sharing and thread synchronization features to allow more effective parallel programming methods. You call the [**ID3D11DeviceContext::Dispatch**](./nf-d3d11-id3d11devicecontext-dispatch-d018ddc011.md) or [**ID3D11DeviceContext::DispatchIndirect**](./nf-d3d11-id3d11devicecontext-dispatchindirect-4235550bd7.md) method to execute commands in a compute shader. A compute shader can run on many threads in parallel.

## Using Compute Shader on Direct3D 10.x Hardware

A compute shader on Microsoft Direct3D 10 is also known as DirectCompute 4.x.

If you use the Direct3D 11 API and updated drivers, [feature level](./overviews-direct3d-11-devices-downlevel-intro-f595280e88.md) 10 and 10.1 Direct3D hardware can optionally support a limited form of DirectCompute that uses the cs\_4\_0 and cs\_4\_1 [profiles](/windows/desktop/direct3dhlsl/dx-graphics-hlsl-models). When you use DirectCompute on this hardware, keep the following limitations in mind:

-   The maximum number of threads is limited to D3D11\_CS\_4\_X\_THREAD\_GROUP\_MAX\_THREADS\_PER\_GROUP (768) per group.
-   The X and Y dimension of **numthreads** is limited to D3D11\_CS\_4\_X\_THREAD\_GROUP\_MAX\_X (768) and D3D11\_CS\_4\_X\_THREAD\_GROUP\_MAX\_Y (768).
-   The Z dimension of **numthreads** is limited to 1.
-   The Z dimension of dispatch is limited to D3D11\_CS\_4\_X\_DISPATCH\_MAX\_THREAD\_GROUPS\_IN\_Z\_DIMENSION (1).
-   Only one unordered-access view can be bound to the shader (D3D11\_CS\_4\_X\_UAV\_REGISTER\_COUNT is 1).
-   Only [RWStructuredBuffer](/windows/desktop/direct3dhlsl/sm5-object-rwstructuredbuffer)s and [RWByteAddressBuffer](/windows/desktop/direct3dhlsl/sm5-object-rwbyteaddressbuffer)s are available as unordered-access views.
-   A thread can only access its own region in groupshared memory for writing, though it can read from any location.
-   [SV\_GroupIndex](/previous-versions/windows/desktop/legacy/ff471569(v=vs.85)) or [SV\_GroupThreadID](/windows/desktop/direct3dhlsl/sv-groupthreadid) must be used when accessing **groupshared** memory for writing.
-   **Groupshared** memory is limited to 16KB per group.
-   A single thread is limited to a 256 byte region of **groupshared** memory for writing.
-   No atomic instructions are available.
-   No double-precision values are available.

## Using Compute Shader on Direct3D 11.x Hardware

A compute shader on Direct3D 11 is also known as DirectCompute 5.0.

When you use DirectCompute with cs\_5\_0 [profiles](/windows/desktop/direct3dhlsl/dx-graphics-hlsl-models), keep the following items in mind:

-   The maximum number of threads is limited to D3D11\_CS\_THREAD\_GROUP\_MAX\_THREADS\_PER\_GROUP (1024) per group.
-   The X and Y dimension of **numthreads** is limited to D3D11\_CS\_THREAD\_GROUP\_MAX\_X (1024) and D3D11\_CS\_THREAD\_GROUP\_MAX\_Y (1024).
-   The Z dimension of **numthreads** is limited to D3D11\_CS\_THREAD\_GROUP\_MAX\_Z (64).
-   The maximum dimension of dispatch is limited to D3D11\_CS\_DISPATCH\_MAX\_THREAD\_GROUPS\_PER\_DIMENSION (65535).
-   The maximum number of unordered-access views that can be bound to a shader is D3D11\_PS\_CS\_UAV\_REGISTER\_COUNT (8).
-   Supports [RWStructuredBuffer](/windows/desktop/direct3dhlsl/sm5-object-rwstructuredbuffer)s, [RWByteAddressBuffer](/windows/desktop/direct3dhlsl/sm5-object-rwbyteaddressbuffer)s, and typed unordered-access views ([RWTexture1D](/windows/desktop/direct3dhlsl/sm5-object-rwtexture1d), [RWTexture2D](/windows/desktop/direct3dhlsl/sm5-object-rwtexture2d), [RWTexture3D](/windows/desktop/direct3dhlsl/sm5-object-rwtexture3d), and so on).
-   Atomic instructions are available.
-   Double-precision support might be available. For information about how to determine whether double-precision is available, see [**D3D11\_FEATURE\_DOUBLES**](./ne-d3d11-d3d11_feature-a05a7560bc.md).

## In this section



| Topic                                                                              | Description                                                                                                                                                                                                                                                           |
|------------------------------------------------------------------------------------|-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| [New Resource Types](./direct3d-11-advanced-stages-cs-resources-7135668641.md)<br/>      | Several new resource types have been added in Direct3D 11.<br/>                                                                                                                                                                                                 |
| [Accessing Resources](./direct3d-11-advanced-stages-cs-access-3ceb1cde93.md)<br/>        | There are several ways to access [resources](./overviews-direct3d-11-resources-types-0fad49d3cf.md).<br/>                                                                                                                                                                   |
| [Atomic Functions](./direct3d-11-advanced-stages-cs-atomic-functions-6e1488b6db.md)<br/> | To access a new resource type or shared memory, use an interlocked intrinsic function. Interlocked functions are guaranteed to operate atomically. That is, they are guaranteed to occur in the order programmed. This section lists the atomic functions.<br/> |



 

## Related topics

<dl> <dt>

[Graphics Pipeline](./overviews-direct3d-11-graphics-pipeline-afe69eb859.md)
</dt> <dt>

[How To: Create a Compute Shader](./direct3d-11-advanced-stages-compute-create-c4dcf959e8.md)
</dt> </dl>