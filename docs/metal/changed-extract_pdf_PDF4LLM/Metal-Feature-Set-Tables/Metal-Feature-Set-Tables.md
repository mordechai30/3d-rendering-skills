Source PDF: <file:///Users/motyzas/metallRef/MetalRefMaterials/Metal-Feature-Set-Tables.pdf>

<a id="page-1"></a>

# Metal Feature Set Tables

##  Developer

<a id="page-2"></a>

### **Metal GPUs (Apple silicon)**

| GPU | Metal version | Apple family 1 |
| --- | --- | --- |
| A8-series | Metal | Apple2 |
| A9-series | Metal | Apple3 |
| A10-series | Metal | Apple3 |
| A11 Bionic | Metal | Apple4 |
| A12-series | Metal | Apple5 |
| A13 Bionic | Metal | Apple6 |
| A14 Bionic | Metal 3 &amp; 4 | Apple7 |
| A15 Bionic | Metal 3 &amp; 4 | Apple8 |
| A16 Bionic | Metal 3 &amp; 4 | Apple8 |
| A17 Pro | Metal 3 &amp; 4 | Apple9 |
| A18-series | Metal 3 &amp; 4 | Apple9 |
| A19-series | Metal 3 &amp; 4 | Apple10 |
| M1-series | Metal 3 &amp; 4 | Apple7 |
| M2-series | Metal 3 &amp; 4 | Apple8 |
| M3-series | Metal 3 &amp; 4 | Apple9 |
| M4-series | Metal 3 &amp; 4 | Apple9 |
| M5-series | Metal 3 &amp; 4 | Apple10 |

### **Metal GPUs (Intel Mac)**

| GPU | Metal version | Mac family 1 |
| --- | --- | --- |
| AMD 500-series | Metal | Mac2 |
| AMD Vega | Metal 3 | Mac2 |
| AMD 5000-series | Metal 3 | Mac2 |
| AMD 6000-series | Metal 3 | Mac2 |
| Intel UHD Graphics 630 | Metal 3 | Mac2 |
| Intel Iris Plus Graphics | Metal 3 | Mac2 |

1. See MTLGPUFamily for each GPU family’s enumeration constant.

For Mac devices with Apple silicon, the MTLDevice instance for the Apple GPU reports that it also supports Mac2 GPU family because the devices support the union of both feature families.

<a id="page-3"></a>

### **Metal feature availability by GPU family**

<table>
<tr>
<th>GPU family 1</th>
<th>Metal</th>
<th>Apple</th>
<th>Mac</th>
</tr>
<tr>
<td>Feature</td>
<td colspan="3">Available in family</td>
</tr>
<tr>
<td>MetalKit</td>
<td>Metal3</td>
<td>Apple2</td>
<td>Mac2</td>
</tr>
<tr>
<td>Metal performance shaders</td>
<td>Metal3</td>
<td>Apple2</td>
<td>Mac2</td>
</tr>
<tr>
<td>Programmable blending</td>
<td>Metal4</td>
<td>Apple2</td>
<td>—</td>
</tr>
<tr>
<td>Separate depth and stencil attachments</td>
<td>Metal4</td>
<td>Apple2</td>
<td>—</td>
</tr>
<tr>
<td>PVRTC pixel formats</td>
<td>—</td>
<td>Apple2</td>
<td>—</td>
</tr>
<tr>
<td>EAC/ETC pixel formats</td>
<td>Metal4</td>
<td>Apple2</td>
<td>—</td>
</tr>
<tr>
<td>ASTC pixel formats</td>
<td>Metal4</td>
<td>Apple2</td>
<td>—</td>
</tr>
<tr>
<td>BC pixel formats 2</td>
<td>—</td>
<td>Apple9</td>
<td>Mac2</td>
</tr>
<tr>
<td>Compressed volume texture formats</td>
<td>Metal3</td>
<td>Apple3</td>
<td>Mac2</td>
</tr>
<tr>
<td>Extended range pixel formats</td>
<td>Metal4</td>
<td>Apple3</td>
<td>—</td>
</tr>
<tr>
<td>Wide color pixel format</td>
<td>Metal3</td>
<td>Apple2</td>
<td>Mac2</td>
</tr>
<tr>
<td>Depth-16 pixel format</td>
<td>Metal3</td>
<td>Apple2</td>
<td>Mac2</td>
</tr>
<tr>
<td>Linear textures</td>
<td>Metal3</td>
<td>Apple2</td>
<td>Mac2</td>
</tr>
<tr>
<td>MSAA depth resolve</td>
<td>Metal3</td>
<td>Apple3</td>
<td>Mac2</td>
</tr>
<tr>
<td>Array of textures (read)</td>
<td>Metal3</td>
<td>Apple3</td>
<td>Mac2</td>
</tr>
<tr>
<td>Array of textures (write)</td>
<td>Metal3</td>
<td>Apple6</td>
<td>Mac2</td>
</tr>
<tr>
<td>Cube map texture arrays</td>
<td>Metal3</td>
<td>Apple4</td>
<td>Mac2</td>
</tr>
<tr>
<td>Stencil texture views</td>
<td>Metal3</td>
<td>Apple2</td>
<td>Mac2</td>
</tr>
<tr>
<td>Array of samplers</td>
<td>Metal3</td>
<td>Apple3</td>
<td>Mac2</td>
</tr>
<tr>
<td>Sampler maximum anisotropy</td>
<td>Metal3</td>
<td>Apple2</td>
<td>Mac2</td>
</tr>
<tr>
<td>Sampler LOD clamp</td>
<td>Metal3</td>
<td>Apple2</td>
<td>Mac2</td>
</tr>
<tr>
<td>MTLSamplerState support for comparison functions</td>
<td>Metal3</td>
<td>Apple3</td>
<td>Mac2</td>
</tr>
<tr>
<td>16-bit unsigned integer coordinates</td>
<td>Metal3</td>
<td>Apple2</td>
<td>Mac2</td>
</tr>
<tr>
<td>Border color</td>
<td>Metal3</td>
<td>Apple7</td>
<td>Mac2</td>
</tr>
<tr>
<td>Counting occlusion query</td>
<td>Metal3</td>
<td>Apple3</td>
<td>Mac2</td>
</tr>
<tr>
<td>Base vertex/instance drawing</td>
<td>Metal3</td>
<td>Apple3</td>
<td>Mac2</td>
</tr>
<tr>
<td>Layered rendering</td>
<td>Metal3</td>
<td>Apple5</td>
<td>Mac2</td>
</tr>
<tr>
<td>Layered rendering to multisample textures</td>
<td>Metal3</td>
<td>Apple7</td>
<td>Mac2</td>
</tr>
<tr>
<td>Memoryless render targets</td>
<td>Metal4</td>
<td>Apple2</td>
<td>—</td>
</tr>
<tr>
<td>Dual-source blending</td>
<td>Metal3</td>
<td>Apple2</td>
<td>Mac2</td>
</tr>
<tr>
<td>Combined MSAA store and resolve action</td>
<td>Metal3</td>
<td>Apple3</td>
<td>Mac2</td>
</tr>
<tr>
<td>MSAA blits</td>
<td>Metal3</td>
<td>Apple2</td>
<td>Mac2</td>
</tr>
<tr>
<td>Programmable sample positions</td>
<td>Metal3</td>
<td>Apple2</td>
<td>Mac2</td>
</tr>
<tr>
<td>Deferred store action</td>
<td>Metal3</td>
<td>Apple2</td>
<td>Mac2</td>
</tr>
<tr>
<td>Texture barriers</td>
<td>—</td>
<td>—</td>
<td>Mac2</td>
</tr>
<tr>
<td>Memory barriers 3</td>
<td>Metal3</td>
<td>Apple3</td>
<td>Mac2</td>
</tr>
<tr>
<td>Indirect command buffer support for memory barriers (compute)</td>
<td>Metal3</td>
<td>Apple3</td>
<td>Mac2</td>
</tr>
<tr>
<td>Indirect command buffer support for memory barriers (rendering)</td>
<td>Metal4</td>
<td>Apple9</td>
<td>—</td>
</tr>
<tr>
<td>Tessellation</td>
<td>Metal3</td>
<td>Apple3</td>
<td>Mac2</td>
</tr>
<tr>
<td>Indirect tessellation arguments</td>
<td>Metal3</td>
<td>Apple5</td>
<td>Mac2</td>
</tr>
<tr>
<td>Tessellation in indirect command buffers</td>
<td>Metal3</td>
<td>Apple5</td>
<td>Mac2</td>
</tr>
<tr>
<td>Resource heaps</td>
<td>Metal3</td>
<td>Apple2</td>
<td>Mac2</td>
</tr>
<tr>
<td>Function specialization</td>
<td>Metal3</td>
<td>Apple2</td>
<td>Mac2</td>
</tr>
<tr>
<td>Read/write buffers in functions</td>
<td>Metal3</td>
<td>Apple3</td>
<td>Mac2</td>
</tr>
<tr>
<td>Read/write textures in functions</td>
<td>Metal3</td>
<td>Apple4</td>
<td>Mac2</td>
</tr>
<tr>
<td>Extract, insert, and reverse bits</td>
<td>Metal3</td>
<td>Apple2</td>
<td>Mac2</td>
</tr>
<tr>
<td>SIMD barrier</td>
<td>Metal3</td>
<td>Apple2</td>
<td>Mac2</td>
</tr>
<tr>
<td>Indirect draw and dispatch arguments</td>
<td>Metal3</td>
<td>Apple3</td>
<td>Mac2</td>
</tr>
<tr>
<td>Argument buffers tier 1</td>
<td>Metal3</td>
<td>Apple2</td>
<td>Mac2</td>
</tr>
<tr>
<td>Argument buffers tier 2</td>
<td>Metal3</td>
<td>Apple6</td>
<td>Mac2</td>
</tr>
<tr>
<td>Indirect command buffers (rendering)</td>
<td>Metal3</td>
<td>Apple3</td>
<td>Mac2</td>
</tr>
<tr>
<td>Indirect command buffers (compute)</td>
<td>Metal3</td>
<td>Apple3</td>
<td>Mac2</td>
</tr>
<tr>
<td>Uniform type</td>
<td>Metal3</td>
<td>Apple2</td>
<td>Mac2</td>
</tr>
<tr>
<td>Imageblocks</td>
<td>Metal4</td>
<td>Apple4</td>
<td>—</td>
</tr>
<tr>
<td>Tile shaders</td>
<td>Metal4</td>
<td>Apple4</td>
<td>—</td>
</tr>
<tr>
<td>Imageblock sample coverage control</td>
<td>Metal4</td>
<td>Apple4</td>
<td>—</td>
</tr>
<tr>
<td>Post-depth coverage</td>
<td>Metal4</td>
<td>Apple4</td>
<td>—</td>
</tr>
<tr>
<td>Quad-scoped permute operations</td>
<td>Metal3</td>
<td>Apple4</td>
<td>Mac2</td>
</tr>
</table>

<a id="page-4"></a>

| GPU family 1 | Metal | Apple | Mac |
| --- | --- | --- | --- |
| Quad-scoped ballot operation | Metal3 | Apple6 | Mac2 |
| Quad-scoped reduction operations | Metal3 | Apple7 | Mac2 |
| SIMD-scoped permute operations | Metal3 | Apple6 | Mac2 |
| SIMD-scoped reduction operations | Metal3 | Apple7 | Mac2 |
| SIMD-scoped matrix multiply operations | Metal4 | Apple7 | — |
| Raster order groups 4 | Metal3 | Apple4 | Varies |
| Nonuniform threadgroup size | Metal3 | Apple4 | Mac2 |
| Multiple viewports | Metal3 | Apple5 | Mac2 |
| Device notifications | — | — | Mac2 |
| Stencil feedback | Metal3 | Apple5 | Mac2 |
| Stencil resolve | Metal3 | Apple5 | Mac2 |
| Nonsquare tile dispatch | Metal4 | Apple5 | — |
| Texture swizzle | Metal3 | Apple2 | Mac2 |
| Placement heap | Metal3 | Apple2 | Mac2 |
| Primitive ID | Metal3 | Apple7 | Mac2 |
| Barycentric coordinates 5 | Metal4 | Apple7 | Varies |
| Read/write cube map textures in functions | Metal3 | Apple4 | Mac2 |
| Sparse textures 6 | Metal4 | Apple6 | — |
| Sparse depth and stencil textures 7 | — | Apple8 | — |
| Variable rasterization rate 8 | Metal4 | Apple6 | Varies |
| Vertex amplification 9 | Metal4 | Apple6 | Varies |
| 64-bit integer math | Metal3 | Apple3 | — |
| Lossy texture compression | — | Apple8 | — |
| SIMD shift and fill | — | Apple8 | — |
| Render dynamic libraries | Metal4 | Apple6 | — |
| Compute dynamic libraries | Metal3 | Apple6 | Mac2 |
| Mesh shading | Metal3 | Apple7 | Mac2 |
| Indirect mesh draw arguments | — | Apple9 | — |
| Indirect command buffers containing mesh draws | — | Apple9 | — |
| MetalFX spatial upscaling | Metal3 | Apple3 | Mac2 |
| MetalFX temporal upscaling | Varies | Apple7 | — |
| MetalFX frame interpolation | Metal4 | Apple5 | — |
| MetalFX denoised upscaling | — | Apple9 | — |
| Fast resource loading | Metal3 | Apple2 | Mac2 |
| Ray tracing in compute pipelines 10 | Metal3 | Apple6 | Varies |
| Ray tracing in render pipelines 11 | Metal4 | Apple6 | — |
| Floating-point atomics | Metal3 | Apple7 | Mac2 |
| Texture atomics | Metal3 | Apple6 | Mac2 |
| 64-bit atomics 12 | — | Apple9 | — |
| Query texture LOD 13 | — | Apple8 | — |
| Binary archives | Metal3 | Apple3 | Mac2 |
| Function pointers in compute pipelines 14 | Metal3 | Apple6 | Varies |
| Function pointers in render pipelines 11 | Metal4 | Apple6 | — |
| Depth sample compare bias and gradient | Metal4 | Apple2 | — |
| Nonprivate depth stencil textures | Metal4 | Apple2 | — |
| Dynamic stride for attribute buffers | Metal3 | Apple4 | Mac2 |
| MTLAttributeFormat.floatRGB9E5 and .floatRG11B10 | Metal3 | Apple5 | Mac2 |
| MTLDataType.bfloat (brain float) scalar and vector cases | Metal3 | Apple6 | Mac2 |
| Relaxed math | Metal4 | Apple4 | — |
| Global built-ins and bindings | Metal4 | Apple6 | — |
| Memory coherence for textures and buffers in shaders | Metal4 | Apple6 | — |
| Per-pipeline shader validation | Metal4 | Apple6 | — |
| Shader logging | Metal4 | Apple6 | — |
| Residency sets | Metal4 | Apple6 | — |
| Acceleration structures containing row-major matrices | — | Apple9 | — |
| Ray tracing with per-component motion interpolation | — | Apple9 | — |
| Direct access to on-chip ray-intersection result storage | — | Apple9 | — |
| Fragment visibility count accumulation 15 | Metal4 | Apple7 | — |
| Argument tables | Metal4 | Apple7 | — |
| Command allocators | Metal4 | Apple7 | — |

<a id="page-5"></a>

| GPU family 1 | Metal | Apple | Mac |
| --- | --- | --- | --- |
| Decoupled command queues and command buffers | Metal4 | Apple7 | — |
| Texture view pools | Metal4 | Apple7 | — |
| Command barriers | Metal4 | Apple7 | — |
| Placement sparse buffers 16 | — | Apple8 | — |
| Placement sparse textures 16 | — | Apple8 | — |
| Dedicated compilation contexts | Metal4 | Apple7 | — |
| Pipeline dataset serialization | Metal4 | Apple7 | — |
| Flexible render pipeline state | Metal4 | Apple7 | — |
| Color attachment mapping 15 | Metal4 | Apple7 | — |
| Machine learning encoding | Metal4 | Apple7 | — |
| Tensors | Metal4 | Apple7 | — |
| Performance counter heaps | Metal4 | Apple7 | — |
| Address-driven acceleration structure builds | — | Apple9 | — |
| Acceleration structure build options | — | Apple9 | — |
| Intersection function buffers | — | Apple9 | — |
| Sampler minimum and maximum reduction | — | Apple10 | — |
| Sampler LOD bias | — | Apple10 | — |
| Access to pre-raster per-vertex values | — | Apple10 | — |
| Depth bounds testing | — | Apple10 | — |
| Indirect command buffer support for raster and depth/stencil state | — | Apple10 | — |
| Atomics on cube map and cube map array textures | — | Apple10 | — |
| Universal texture compression | — | Apple10 | — |

1. See [MTLGPUFamily](<https://developer.apple.com/documentation/metal/mtlgpufamily>) for each GPU family’s enumeration constant.

2. Some GPU devices in the Apple7 and Apple8 families support BC texture compression in iPadOS. You can check an individual GPU’s support for this feature by inspecting its MTLDevice.supportsBCTextureCompression property at runtime.  As of Apple9 all GPUs have support.

3. GPU devices in Apple3 through Apple10 families don’t support memory barriers that include the MTLRenderStages.fragment or .tile stages in the after argument, or MTLBarrierScope.renderTargets in the scope argument of MTLRenderCommandEncoder.memoryBarrier(scope:after:before:) and MTLRenderCommandEncoder.memoryBarrier(resources:after:before:).

4. Some GPU devices in the Mac2 family support raster order groups. You can check an individual GPU’s support for this feature by inspecting its MTLDevice.rasterOrderGroupsSupported property at runtime.

5. Some GPU devices in the Mac2 and Metal3 families support barycentric coordinates. You can check an individual GPU’s support for this feature by inspecting its MTLDevice.supportsShaderBarycentricCoordinates property at runtime.

6. GPU devices starting with the Apple6 family support sparse color textures with automatic heap backing. Automatic heap backing doesn’t support sparse buffers or sparse textures with 1D, 1DArray, or TextureBuffer texture types.

7. Some GPU devices in the Apple7 family, including all Apple7 MacOS devices, support sparse depth and stencil textures with placement heap backing. You can check an individual GPU’s support for this feature by inspecting its MTLDevice.supportsPlacementSparse property at runtime. As of Apple8, all GPUs have support for both placement and automatic heap backing for sparse color, depth, and stencil textures.

8. Some GPU devices in the Mac2 family support variable rasterization rates. You can check an individual GPU’s support for this feature by calling its MTLDevice.supportsRasterizationRateMap(layerCount:) method at runtime.

9. Some GPU devices in the Mac2 family support vertex amplification. You can check an individual GPU’s support for this feature by calling its MTLDevice.supportsVertexAmplificationCount(\_:) method at runtime.

10. Some GPU devices in the Mac2 family support ray tracing in compute pipelines. You can check an individual GPU’s support for this feature by inspecting its MTLDevice.supportsRaytracing property at runtime.

11. Support for function pointers and ray tracing in render pipelines isn’t compatible with mesh shading. You can only use Metal IR linking through MTLLinkedFunctions.privateFunctions in render pipelines using mesh shading.

12. Some GPU devices in the Apple8 family support 64-bit atomic minimum and maximum using ulong, on both buffers and textures. You can check an individual GPU’s support for this feature by verifying it supports both the Mac2 and Apple8 families by separately passing each to the MTLDevice.supportsFamily(\_:) method.  As of Apple9 all GPUs have support.

13. Some GPU devices in the Apple7 family support query texture LOD. You can check an individual GPU’s support for this feature by inspecting its MTLDevice.supportsQueryTextureLOD property at runtime.  As of Apple8 all GPUs have support.

14. Some GPU devices in the Mac2 family support function pointers in compute pipelines. You can check an individual GPU’s support for this feature by inspecting its MTLDevice.supportsFunctionPointers property at runtime.

15. GPU devices supporting fragment visibility count accumulation and color attachment mapping features support those features in both Metal3 and Metal4 command encoding models.

16. Some GPU devices in the Apple7 family, including all Apple7 MacOS devices, support sparse buffers and textures with placement heap backing. You can check an individual GPU’s support for this feature by inspecting its MTLDevice.supportsPlacementSparse property at runtime. As of Apple8 all GPUs have support.

<a id="page-6"></a>

### **GPU implementation limits by family**

<table>
<tr>
<th>GPU family 1</th>
<th>Metal3</th>
<th>Metal4</th>
<th>Apple2</th>
<th>Apple3</th>
<th>Apple4</th>
<th>Apple5</th>
<th>Apple6</th>
<th>Apple7</th>
<th>Apple8</th>
<th>Apple9</th>
<th>Apple10</th>
<th>Mac2</th>
</tr>
<tr>
<td>Function arguments</td>
<td colspan="12">Function arguments</td>
</tr>
<tr>
<td>Maximum number of vertex attributes, per vertex descriptor 2</td>
<td>31</td>
<td>31</td>
<td>31</td>
<td>31</td>
<td>31</td>
<td>31</td>
<td>31</td>
<td>31</td>
<td>31</td>
<td>31</td>
<td>31</td>
<td>31</td>
</tr>
<tr>
<td>Maximum number of entries in the buffer argument table, per graphics or kernel function 2</td>
<td>31</td>
<td>31</td>
<td>31</td>
<td>31</td>
<td>31</td>
<td>31</td>
<td>31</td>
<td>31</td>
<td>31</td>
<td>31</td>
<td>31</td>
<td>31</td>
</tr>
<tr>
<td>Maximum number of entries in the texture argument table, per graphics or kernel function 2</td>
<td>128</td>
<td>128</td>
<td>31</td>
<td>31</td>
<td>96</td>
<td>96</td>
<td>128</td>
<td>128</td>
<td>128</td>
<td>128</td>
<td>128</td>
<td>128</td>
</tr>
<tr>
<td>Maximum number of entries in the sampler state argument table, per graphics or kernel functions 2 3</td>
<td>16</td>
<td>16</td>
<td>16</td>
<td>16</td>
<td>16</td>
<td>16</td>
<td>16</td>
<td>16</td>
<td>16</td>
<td>16</td>
<td>16</td>
<td>16</td>
</tr>
<tr>
<td>Maximum number of entries in the threadgroup memory argument table, per kernel function 2</td>
<td>31</td>
<td>31</td>
<td>31</td>
<td>31</td>
<td>31</td>
<td>31</td>
<td>31</td>
<td>31</td>
<td>31</td>
<td>31</td>
<td>31</td>
<td>31</td>
</tr>
<tr>
<td>Maximum number of constant buffer arguments in vertex, fragment, tile, or kernel functions 2</td>
<td>14</td>
<td>31</td>
<td>31</td>
<td>31</td>
<td>31</td>
<td>31</td>
<td>31</td>
<td>31</td>
<td>31</td>
<td>31</td>
<td>31</td>
<td>14</td>
</tr>
<tr>
<td>Maximum length of inlined buffer contents using setBytes 4</td>
<td>4 KB</td>
<td>4 KB</td>
<td>4 KB</td>
<td>4 KB</td>
<td>4 KB</td>
<td>4 KB</td>
<td>4 KB</td>
<td>4 KB</td>
<td>4 KB</td>
<td>4 KB</td>
<td>4 KB</td>
<td>4 KB</td>
</tr>
<tr>
<td>Maximum threads per threadgroup 5</td>
<td>1024</td>
<td>1024</td>
<td>512</td>
<td>512</td>
<td>1024</td>
<td>1024</td>
<td>1024</td>
<td>1024</td>
<td>1024</td>
<td>1024</td>
<td>1024</td>
<td>1024</td>
</tr>
<tr>
<td>Maximum total threadgroup memory allocation</td>
<td>32 KB</td>
<td>32 KB</td>
<td>16,352 B</td>
<td>16 KB</td>
<td>32 KB</td>
<td>32 KB</td>
<td>32 KB</td>
<td>32 KB</td>
<td>32 KB</td>
<td>32 KB</td>
<td>32 KB</td>
<td>32 KB</td>
</tr>
<tr>
<td>Maximum explicit image block allocation 6</td>
<td>Not available</td>
<td>32 KB</td>
<td>Not available</td>
<td>Not available</td>
<td>32 KB</td>
<td>32 KB</td>
<td>32 KB</td>
<td>32 KB</td>
<td>32 KB</td>
<td>32 KB</td>
<td>32 KB</td>
<td>Not available</td>
</tr>
<tr>
<td>Maximum implicit image block allocation 6</td>
<td>Not available</td>
<td>128 KB</td>
<td>Not available</td>
<td>Not available</td>
<td>128 KB</td>
<td>128 KB</td>
<td>128 KB</td>
<td>128 KB</td>
<td>128 KB</td>
<td>256 KB</td>
<td>256 KB</td>
<td>Not available</td>
</tr>
<tr>
<td>Threadgroup memory length alignment</td>
<td>16 B</td>
<td>16 B</td>
<td>16 B</td>
<td>16 B</td>
<td>16 B</td>
<td>16 B</td>
<td>16 B</td>
<td>16 B</td>
<td>16 B</td>
<td>16 B</td>
<td>16 B</td>
<td>16 B</td>
</tr>
<tr>
<td>Maximum scalar or vector inputs to a fragment function. (Declare with the [[stage_in]] qualifier.) 7</td>
<td>32</td>
<td>124</td>
<td>60</td>
<td>60</td>
<td>124</td>
<td>124</td>
<td>124</td>
<td>124</td>
<td>124</td>
<td>124</td>
<td>124</td>
<td>32</td>
</tr>
<tr>
<td>Maximum number of input components to a fragment function. (Declare with the [[stage_in]] qualifier.) 7</td>
<td>124</td>
<td>124</td>
<td>60</td>
<td>60</td>
<td>124</td>
<td>124</td>
<td>124</td>
<td>124</td>
<td>124</td>
<td>124</td>
<td>124</td>
<td>124</td>
</tr>
<tr>
<td>Maximum number of function constants</td>
<td>65,536</td>
<td>65,536</td>
<td>65,536</td>
<td>65,536</td>
<td>65,536</td>
<td>65,536</td>
<td>65,536</td>
<td>65,536</td>
<td>65,536</td>
<td>65,536</td>
<td>65,536</td>
<td>65,536</td>
</tr>
<tr>
<td>Maximum tessellation factor</td>
<td>64</td>
<td>64</td>
<td>Not available</td>
<td>16</td>
<td>16</td>
<td>64</td>
<td>64</td>
<td>64</td>
<td>64</td>
<td>64</td>
<td>64</td>
<td>64</td>
</tr>
<tr>
<td>Maximum number of viewports and scissor rectangles, per vertex function</td>
<td>16</td>
<td>16</td>
<td>1</td>
<td>1</td>
<td>1</td>
<td>16</td>
<td>16</td>
<td>16</td>
<td>16</td>
<td>16</td>
<td>16</td>
<td>16</td>
</tr>
<tr>
<td>Maximum number of raster order groups, per fragment function</td>
<td>8</td>
<td>8</td>
<td>Not available</td>
<td>Not available</td>
<td>8</td>
<td>8</td>
<td>8</td>
<td>8</td>
<td>8</td>
<td>8</td>
<td>8</td>
<td>8</td>
</tr>
<tr>
<td>Minimum alignment of buffer layout descriptor stride and attribute descriptor offset</td>
<td>4 B</td>
<td>1 B</td>
<td>4 B</td>
<td>4 B</td>
<td>4 B</td>
<td>1 B</td>
<td>1 B</td>
<td>1 B</td>
<td>1 B</td>
<td>1 B</td>
<td>1 B</td>
<td>4 B</td>
</tr>
<tr>
<td>Maximum size of buffer layout descriptor stride</td>
<td>4 KB</td>
<td>No limit</td>
<td>No limit</td>
<td>No limit</td>
<td>No limit</td>
<td>No limit</td>
<td>No limit</td>
<td>No limit</td>
<td>No limit</td>
<td>No limit</td>
<td>No limit</td>
<td>4 KB</td>
</tr>
<tr>
<td>Argument buffers 8</td>
<td colspan="12">Argument buffers</td>
</tr>
<tr>
<td>Maximum number of buffers you can access, per stage, from an argument buffer</td>
<td>No limit</td>
<td>No limit</td>
<td>31</td>
<td>31</td>
<td>96</td>
<td>96</td>
<td>No limit</td>
<td>No limit</td>
<td>No limit</td>
<td>No limit</td>
<td>No limit</td>
<td>No limit</td>
</tr>
<tr>
<td>Maximum number of textures you can access, per stage, from an argument buffer</td>
<td>1 M</td>
<td>1 M</td>
<td>31</td>
<td>31</td>
<td>96</td>
<td>96</td>
<td>1 M</td>
<td>1 M</td>
<td>1 M</td>
<td>1 M</td>
<td>1 M</td>
<td>1 M</td>
</tr>
<tr>
<td>Maximum number of samplers you can access, per stage, from an argument buffer</td>
<td>1024</td>
<td>1024</td>
<td>16</td>
<td>16</td>
<td>16</td>
<td>16</td>
<td>128</td>
<td>996</td>
<td>996</td>
<td>500 K</td>
<td>500 K</td>
<td>1024</td>
</tr>
</table>

<a id="page-7"></a>

<table>
<tr>
<th>GPU family 1</th>
<th>Metal3</th>
<th>Metal4</th>
<th>Apple2</th>
<th>Apple3</th>
<th>Apple4</th>
<th>Apple5</th>
<th>Apple6</th>
<th>Apple7</th>
<th>Apple8</th>
<th>Apple9</th>
<th>Apple10</th>
<th>Mac2</th>
</tr>
<tr>
<td>Resources</td>
<td colspan="12">Resources</td>
</tr>
<tr>
<td>Minimum constant buffer offset alignment</td>
<td>32 B</td>
<td>4 B</td>
<td>4 B</td>
<td>4 B</td>
<td>4 B</td>
<td>4 B</td>
<td>4 B</td>
<td>4 B</td>
<td>4 B</td>
<td>4 B</td>
<td>4 B</td>
<td>32 B</td>
</tr>
<tr>
<td>Maximum 1D texture width</td>
<td>16,384 px</td>
<td>16,384 px</td>
<td>8192 px</td>
<td>16,384 px</td>
<td>16,384 px</td>
<td>16,384 px</td>
<td>16,384 px</td>
<td>16,384 px</td>
<td>16,384 px</td>
<td>16,384 px</td>
<td>32,768 px</td>
<td>16,384 px</td>
</tr>
<tr>
<td>Maximum 2D texture width and height</td>
<td>16,384 px</td>
<td>16,384 px</td>
<td>8192 px</td>
<td>16,384 px</td>
<td>16,384 px</td>
<td>16,384 px</td>
<td>16,384 px</td>
<td>16,384 px</td>
<td>16,384 px</td>
<td>16,384 px</td>
<td>32,768 px</td>
<td>16,384 px</td>
</tr>
<tr>
<td>Maximum cube map texture width and height</td>
<td>16,384 px</td>
<td>16,384 px</td>
<td>8192 px</td>
<td>16,384 px</td>
<td>16,384 px</td>
<td>16,384 px</td>
<td>16,384 px</td>
<td>16,384 px</td>
<td>16,384 px</td>
<td>16,384 px</td>
<td>32,768 px</td>
<td>16,384 px</td>
</tr>
<tr>
<td>Maximum 3D texture width, height, and depth</td>
<td>2048 px</td>
<td>2048 px</td>
<td>2048 px</td>
<td>2048 px</td>
<td>2048 px</td>
<td>2048 px</td>
<td>2048 px</td>
<td>2048 px</td>
<td>2048 px</td>
<td>2048 px</td>
<td>2048 px</td>
<td>2048 px</td>
</tr>
<tr>
<td>Maximum texture buffer width 9</td>
<td>256 M px</td>
<td>256 M px</td>
<td>64 M px</td>
<td>256 M px</td>
<td>256 M px</td>
<td>256 M px</td>
<td>256 M px</td>
<td>256 M px</td>
<td>256 M px</td>
<td>256 M px</td>
<td>256 M px</td>
<td>256 M px</td>
</tr>
<tr>
<td>Maximum number of layers per 1D texture array, 2D texture array, or 3D texture array</td>
<td>2048</td>
<td>2048</td>
<td>2048</td>
<td>2048</td>
<td>2048</td>
<td>2048</td>
<td>2048</td>
<td>2048</td>
<td>2048</td>
<td>2048</td>
<td>2048</td>
<td>2048</td>
</tr>
<tr>
<td>Buffer alignment for copying an existing texture to a buffer</td>
<td>256 B</td>
<td>16 B</td>
<td>64 B</td>
<td>16 B</td>
<td>16 B</td>
<td>16 B</td>
<td>16 B</td>
<td>16 B</td>
<td>16 B</td>
<td>16 B</td>
<td>16 B</td>
<td>256 B</td>
</tr>
<tr>
<td>Maximum counter sample buffer length</td>
<td>32 KB</td>
<td>32 KB</td>
<td>32 KB</td>
<td>32 KB</td>
<td>32 KB</td>
<td>32 KB</td>
<td>32 KB</td>
<td>32 KB</td>
<td>32 KB</td>
<td>32 KB</td>
<td>32 KB</td>
<td>No limit</td>
</tr>
<tr>
<td>Maximum number of sample buffers</td>
<td>32</td>
<td>32</td>
<td>32</td>
<td>32</td>
<td>32</td>
<td>32</td>
<td>32</td>
<td>32</td>
<td>32</td>
<td>32</td>
<td>32</td>
<td>No limit</td>
</tr>
<tr>
<td>Maximum number of residency sets per queue</td>
<td>32</td>
<td>32</td>
<td>Not available</td>
<td>Not available</td>
<td>Not available</td>
<td>Not available</td>
<td>32</td>
<td>32</td>
<td>32</td>
<td>32</td>
<td>32</td>
<td>32</td>
</tr>
<tr>
<td>Maximum number of residency sets per buffer</td>
<td>32</td>
<td>32</td>
<td>Not available</td>
<td>Not available</td>
<td>Not available</td>
<td>Not available</td>
<td>32</td>
<td>32</td>
<td>32</td>
<td>32</td>
<td>32</td>
<td>32</td>
</tr>
<tr>
<td>Maximum indirect command buffer length</td>
<td>16,384 commands</td>
<td>No limit</td>
<td>Not available</td>
<td>No limit</td>
<td>No limit</td>
<td>No limit</td>
<td>No limit</td>
<td>No limit</td>
<td>No limit</td>
<td>No limit</td>
<td>No limit</td>
<td>16,384 commands</td>
</tr>
<tr>
<td>Render targets</td>
<td colspan="12">Render targets</td>
</tr>
<tr>
<td>Maximum number of color render targets per render pass descriptor</td>
<td>8</td>
<td>8</td>
<td>8</td>
<td>8</td>
<td>8</td>
<td>8</td>
<td>8</td>
<td>8</td>
<td>8</td>
<td>8</td>
<td>8</td>
<td>8</td>
</tr>
<tr>
<td>Maximum size of a point primitive</td>
<td>511</td>
<td>511</td>
<td>511</td>
<td>511</td>
<td>511</td>
<td>511</td>
<td>511</td>
<td>511</td>
<td>511</td>
<td>511</td>
<td>511</td>
<td>511</td>
</tr>
<tr>
<td>Maximum explicit image block size, per pixel, per sample, when using multiple color render targets</td>
<td>Not available</td>
<td>64 B</td>
<td>Not available</td>
<td>Not available</td>
<td>64 B</td>
<td>64 B</td>
<td>64 B</td>
<td>64 B</td>
<td>64 B</td>
<td>64 B</td>
<td>64 B</td>
<td>Not available</td>
</tr>
<tr>
<td>Maximum implicit image block size, per pixel, per sample, when using multiple color render targets</td>
<td>Not available</td>
<td>128 B</td>
<td>32 B</td>
<td>32 B</td>
<td>64 B</td>
<td>64 B</td>
<td>64 B</td>
<td>128 B</td>
<td>128 B</td>
<td>128 B</td>
<td>128 B</td>
<td>Not available</td>
</tr>
<tr>
<td>Maximum visibility query offset</td>
<td>256 KB</td>
<td>256 KB</td>
<td>65,528 B</td>
<td>65,528 B</td>
<td>65,528 B</td>
<td>65,528 B</td>
<td>65,528 B</td>
<td>256 KB</td>
<td>256 KB</td>
<td>256 KB</td>
<td>256 KB</td>
<td>256 KB</td>
</tr>
<tr>
<td>Maximum sample count in render passes with MSAA</td>
<td>4</td>
<td>4</td>
<td>4</td>
<td>4</td>
<td>4</td>
<td>4</td>
<td>4</td>
<td>4</td>
<td>4</td>
<td>4</td>
<td>8</td>
<td>4</td>
</tr>
<tr>
<td>Maximum tile size in render passes without MSAA</td>
<td>Not available</td>
<td>32 x 32</td>
<td>32 x 32</td>
<td>32 x 32</td>
<td>32 x 32</td>
<td>32 x 32</td>
<td>32 x 32</td>
<td>32 x 32</td>
<td>32 x 32</td>
<td>32 x 32</td>
<td>32 x 32</td>
<td>Not available</td>
</tr>
<tr>
<td>Maximum tile size in render passes with 2x MSAA</td>
<td>Not available</td>
<td>32 x 32</td>
<td>32 x 32</td>
<td>32 x 32</td>
<td>32 x 32</td>
<td>32 x 32</td>
<td>32 x 32</td>
<td>32 x 32</td>
<td>32 x 32</td>
<td>32 x 32</td>
<td>32 x 32</td>
<td>Not available</td>
</tr>
<tr>
<td>Maximum tile size in render passes with 4x MSAA</td>
<td>Not available</td>
<td>32 x 16</td>
<td>32 x 16</td>
<td>32 x 16</td>
<td>32 x 16</td>
<td>32 x 16</td>
<td>32 x 16</td>
<td>32 x 16</td>
<td>32 x 16</td>
<td>32 x 16</td>
<td>32 x 16</td>
<td>Not available</td>
</tr>
<tr>
<td>Maximum tile size in render passes with 8x MSAA</td>
<td>Not available</td>
<td>Not available</td>
<td>Not available</td>
<td>Not available</td>
<td>Not available</td>
<td>Not available</td>
<td>Not available</td>
<td>Not available</td>
<td>Not available</td>
<td>Not available</td>
<td>16 x 16</td>
<td>Not available</td>
</tr>
<tr>
<td>Feature limits</td>
<td colspan="12">Feature limits</td>
</tr>
</table>

<a id="page-8"></a>

| GPU family 1 | Metal3 | Metal4 | Apple2 | Apple3 | Apple4 | Apple5 | Apple6 | Apple7 | Apple8 | Apple9 | Apple10 | Mac2 |
| --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- |
| Maximum number of fences | 32,768 | 32,768 | 32,768 | 32,768 | 32,768 | 32,768 | 32,768 | 32,768 | 32,768 | 32,768 | 32,768 | 32,768 |
| Maximum number of I/O commands per buffer | 8192 | 8192 | 8192 | 8192 | 8192 | 8192 | 8192 | 8192 | 8192 | 8192 | 8192 | 8192 |
| Maximum vertex count for vertex amplification 10 | Varies | 8 | Not available | Not available | Not available | Not available | 2 | 8 | 8 | 8 | 8 | Varies |
| Maximum threadgroups per object shader grid | 1024 | No limit | Not available | Not available | Not available | Not available | Not available | No limit | No limit | No limit | No limit | 1024 |
| Maximum threadgroups per mesh shader grid 11 | 1024 | 1024 | Not available | Not available | Not available | Not available | Not available | 1024 | 1024 | 1,048,575 | 4,194,303 | 1024 |
| Maximum payload in mesh shader pipeline 12 | 16,384 B | 16,384 B | Not available | Not available | Not available | Not available | Not available | 16,384 B | 16,384 B | 16,384 B | 16,384 B | 16,384 B |
| Largest number of levels a ray-tracing intersector can traverse in an acceleration structure 13 | 32 | 32 | Not available | Not available | Not available | Not available | 32 | 32 | 32 | 32 | 32 | 32 |
| Largest number of levels a ray-tracing intersection query can traverse in an acceleration structure 13 | 16 | 16 | Not available | Not available | Not available | Not available | 16 | 16 | 16 | 16 | 16 | 16 |
| Maximum texture view pool entries | Not available | 128 million | Not available | Not available | Not available | Not available | Not available | 128 million | 128 million | 256 million | 256 million | Not available |
| Maximum supported tensor rank | Not available | 16 | Not available | Not available | Not available | Not available | Not available | 16 | 16 | 16 | 16 | Not available |
| Maximum supported tensor stride at dimension index 0 for machine learning encoder usage | Not available | 1 element | Not available | Not available | Not available | Not available | Not available | 1 element | 1 element | 1 element | 1 element | Not available |
| Minimum alignment of tensor stride at dimension index 1 for machine learning encoder usage | Not available | 64 B | Not available | Not available | Not available | Not available | Not available | 64 B | 64 B | 64 B | 64 B | Not available |
| Maximum performance counter heaps (per process) | Not available | 32 | Not available | Not available | Not available | Not available | Not available | 32 | 32 | 32 | 32 | Not available |
| Minimum alignment of intersection function buffer | Not available | 64 B | Not available | Not available | Not available | Not available | Not available | 64 B | 64 B | 64 B | 64 B | Not available |
| Minimum alignment of intersection function buffer stride | Not available | 8 B | Not available | Not available | Not available | Not available | Not available | 8 B | 8 B | 8 B | 8 B | Not available |
| Maximum size of intersection function buffer stride | Not available | 4096 B | Not available | Not available | Not available | Not available | Not available | 4096 B | 4096 B | 4096 B | 4096 B | Not available |

1. See [MTLGPUFamily](<https://developer.apple.com/documentation/metal/mtlgpufamily>) for each GPU family’s enumeration constant.

2. These values are identical to the maximum number of bindings in an MTL4ArgumentTable of the same type.

3. Inline constexpr samplers that you declare in [Metal Shading Language](<https://developer.apple.com/metal/Metal-Shading-Language-Specification.pdf>) (MSL) code count toward the limit. For example, for a feature set limit of 16, you can have 12 API samplers and 4 language samplers (16 total), but you can’t have 12 API samplers and 6 language samplers (18 total).

4. Inlined buffer contents populate through functions like [setBytes,](<https://developer.apple.com/documentation/metal/mtlcomputecommandencoder/setbytes(_:length:index:)>) and its variants for specific render stages. Noninlined buffer contents that you access through [MTLBuffer](<https://developer.apple.com/documentation/metal/mtlbuffer>) or it’s GPU virtual address are limited only by the size of that buffer.

5. The values in this row are the theoretical maximum number of threads per threadgroup. Check the actual maximum by inspecting the MTLComputePipelineState.maxTotalThreadsPerThreadgroup property at runtime.

6. You can allocate memory between imageblock and threadgroup memory, but the sum of these allocations can’t exceed the maximum total image block memory limit. Some feature sets can’t access image block memory directly, but they can access threadgroup memory. Which image block memory limit applies depends on the shader’s usage of either implicit or explicit image block layout; see the Metal Shading Language specification for details.

7. A vector counts as n scalars, where n is the number of components in the vector. The iOS and tvOS feature sets only reach the maximum number of inputs if you don’t exceed the maximum number of input components. For example, you can have 60 float inputs (components), but you can’t have 60 float4 inputs, which total 240 components.

8. The limits apply to the items you place in the argument buffers you bind directly and in the argument buffers you can access indirectly through your bound argument buffers.

9. The maximum texture buffer width, in pixels, is also limited by MTLDevice.maxBufferLength divided by the size of a pixel, in bytes, as well as available memory.

10. Some GPU devices in the [Mac2](<https://developer.apple.com/documentation/metal/mtlgpufamily/mac2>) family support vertex amplification. You can check an individual GPU’s support for this feature by calling its MTLDevice.supportsVertexAmplificationCount(\_:) method at runtime.

11. Mesh shaders can use up to 4 GB of payload and mesh geometry per draw for devices in the [Apple7](<https://developer.apple.com/documentation/metal/mtlgpufamily/apple7>) and [Apple8](<https://developer.apple.com/documentation/metal/mtlgpufamily/apple8>) GPU families.

12. Mesh shaders that have a [[threadgroups\_per\_grid]] or [[threads\_per\_grid]] parameter reduce the available payload size by 16 bytes. Viewing a mesh shader’s geometry in the Metal debugger (within Xcode) reduces the available payload by 16 bytes. The total payload size reduction can be 32 bytes.

13. The value includes one level for the primitive acceleration structure, which leaves the remaining levels for instance acceleration structures.

<a id="page-9"></a>

This table lists the GPU’s texture capabilities for each pixel format: • Atomic: The GPU can use atomic operations on textures with the pixel format.

• All: The GPU has the following texture capabilities for the pixel format: • Filter: The GPU can filter a texture with the pixel format during sampling. • Write: The GPU can write to a texture on a per-pixel basis with the pixel format.2 • Color: The GPU can use a texture with the pixel format as a color render target. • Blend: The GPU can blend a texture with the pixel format. • MSAA: The GPU can use a texture with the pixel format as a destination for multisample antialias (MSAA) data. • Sparse: The GPU supports sparse-texture allocations for textures with the pixel format.                 Sparse isn’t included in All for the Mac2, Metal3, and Apple2 through Apple5 family columns, because those GPUs don’t support the sparse texture feature. • Resolve: The GPU can use a texture with the pixel format as a source for multisample antialias (MSAA) resolve operations.

Note All graphics and compute kernels can read or sample a texture with any pixel format.

### **Texture capabilities by pixel format**

<table>
<tr>
<th>GPU family 1</th>
<th>Metal3</th>
<th>Metal4</th>
<th>Apple2</th>
<th>Apple3</th>
<th>Apple4</th>
<th>Apple5</th>
<th>Apple6</th>
<th>Apple7</th>
<th>Apple8</th>
<th>Apple9</th>
<th>Apple10</th>
<th>Mac2</th>
</tr>
<tr>
<td>Ordinary 8-bit pixel formats</td>
<td colspan="12">Texture capabilities for ordinary 8-bit pixel formats by GPU family</td>
</tr>
<tr>
<td>A8Unorm 2,3</td>
<td>All</td>
<td>All</td>
<td>Filter</td>
<td>All</td>
<td>All</td>
<td>All</td>
<td>All</td>
<td>All</td>
<td>All</td>
<td>All</td>
<td>All</td>
<td>All</td>
</tr>
<tr>
<td>R8Unorm 2</td>
<td>All</td>
<td>All</td>
<td>All</td>
<td>All</td>
<td>All</td>
<td>All</td>
<td>All</td>
<td>All</td>
<td>All</td>
<td>All</td>
<td>All</td>
<td>All</td>
</tr>
<tr>
<td>R8Unorm_sRGB</td>
<td>Not available</td>
<td>All</td>
<td>All</td>
<td>All</td>
<td>All</td>
<td>All</td>
<td>All</td>
<td>All</td>
<td>All</td>
<td>All</td>
<td>All</td>
<td>Not available</td>
</tr>
<tr>
<td>R8Snorm</td>
<td>All</td>
<td>All</td>
<td>All</td>
<td>All</td>
<td>All</td>
<td>All</td>
<td>All</td>
<td>All</td>
<td>All</td>
<td>All</td>
<td>All</td>
<td>All</td>
</tr>
<tr>
<td>R8Uint 2 R8Sint 2</td>
<td>Write Color MSAA</td>
<td>Write Color MSAA Sparse</td>
<td>Write Color MSAA</td>
<td>Write Color MSAA</td>
<td>Write Color MSAA</td>
<td>Write Color MSAA</td>
<td>Write Color MSAA Sparse</td>
<td>Write Color MSAA Sparse</td>
<td>Write Color MSAA Sparse</td>
<td>Write Color MSAA Sparse</td>
<td>Write Color MSAA Sparse</td>
<td>Write Color MSAA</td>
</tr>
<tr>
<td>Ordinary 16-bit pixel formats</td>
<td colspan="12">Texture capabilities for ordinary 16-bit pixel formats by GPU family</td>
</tr>
<tr>
<td>R16Unorm R16Snorm</td>
<td>All</td>
<td>All</td>
<td>Filter Write Color MSAA Blend</td>
<td>Filter Write Color MSAA Blend</td>
<td>All</td>
<td>All</td>
<td>All</td>
<td>All</td>
<td>All</td>
<td>All</td>
<td>All</td>
<td>All</td>
</tr>
<tr>
<td>R16Uint 2 R16Sint 2</td>
<td>Write Color MSAA</td>
<td>Write Color MSAA Sparse</td>
<td>Write Color MSAA</td>
<td>Write Color MSAA</td>
<td>Write Color MSAA</td>
<td>Write Color MSAA</td>
<td>Write Color MSAA Sparse</td>
<td>Write Color MSAA Sparse</td>
<td>Write Color MSAA Sparse</td>
<td>Write Color MSAA Sparse</td>
<td>Write Color MSAA Sparse</td>
<td>Write Color MSAA</td>
</tr>
<tr>
<td>R16Float 2</td>
<td>All</td>
<td>All</td>
<td>All</td>
<td>All</td>
<td>All</td>
<td>All</td>
<td>All</td>
<td>All</td>
<td>All</td>
<td>All</td>
<td>All</td>
<td>All</td>
</tr>
<tr>
<td>RG8Unorm</td>
<td>All</td>
<td>All</td>
<td>All</td>
<td>All</td>
<td>All</td>
<td>All</td>
<td>All</td>
<td>All</td>
<td>All</td>
<td>All</td>
<td>All</td>
<td>All</td>
</tr>
<tr>
<td>RG8Unorm_sRGB</td>
<td>Not available</td>
<td>All</td>
<td>All</td>
<td>All</td>
<td>All</td>
<td>All</td>
<td>All</td>
<td>All</td>
<td>All</td>
<td>All</td>
<td>All</td>
<td>Not available</td>
</tr>
<tr>
<td>RG8Snorm</td>
<td>All</td>
<td>All</td>
<td>All</td>
<td>All</td>
<td>All</td>
<td>All</td>
<td>All</td>
<td>All</td>
<td>All</td>
<td>All</td>
<td>All</td>
<td>All</td>
</tr>
</table>

<a id="page-10"></a>

<table>
<tr>
<th>GPU family 1</th>
<th>Metal3</th>
<th>Metal4</th>
<th>Apple2</th>
<th>Apple3</th>
<th>Apple4</th>
<th>Apple5</th>
<th>Apple6</th>
<th>Apple7</th>
<th>Apple8</th>
<th>Apple9</th>
<th>Apple10</th>
<th>Mac2</th>
</tr>
<tr>
<td>RG8Uint RG8Sint</td>
<td>Write Color MSAA</td>
<td>Write Color MSAA Sparse</td>
<td>Write Color MSAA</td>
<td>Write Color MSAA</td>
<td>Write Color MSAA</td>
<td>Write Color MSAA</td>
<td>Write Color MSAA Sparse</td>
<td>Write Color MSAA Sparse</td>
<td>Write Color MSAA Sparse</td>
<td>Write Color MSAA Sparse</td>
<td>Write Color MSAA Sparse</td>
<td>Write Color MSAA</td>
</tr>
<tr>
<td>Packed 16-bit pixel formats 4</td>
<td colspan="12">Texture capabilities for packed 16-bit pixel formats by GPU family</td>
</tr>
<tr>
<td>B5G6R5Unorm A1BGR5Unorm 5 ABGR4Unorm 5 BGR5A1Unorm</td>
<td>Not available</td>
<td>Filter Color MSAA Resolve Blend Sparse</td>
<td>Filter Color MSAA Resolve Blend</td>
<td>Filter Color MSAA Resolve Blend</td>
<td>Filter Color MSAA Resolve Blend</td>
<td>Filter Color MSAA Resolve Blend</td>
<td>Filter Color MSAA Resolve Blend Sparse</td>
<td>Filter Color MSAA Resolve Blend Sparse</td>
<td>Filter Color MSAA Resolve Blend Sparse</td>
<td>Filter Color MSAA Resolve Blend Sparse</td>
<td>Filter Color MSAA Resolve Blend Sparse</td>
<td>Not available</td>
</tr>
<tr>
<td>Ordinary 32-bit pixel formats</td>
<td colspan="12">Texture capabilities for ordinary 32-bit pixel formats by GPU family</td>
</tr>
<tr>
<td>R32Uint 2 R32Sint 2</td>
<td>Atomic Write Color MSAA</td>
<td>Atomic Write Color MSAA Sparse</td>
<td>Write Color</td>
<td>Write Color</td>
<td>Write Color</td>
<td>Write Color</td>
<td>Atomic Write Color Sparse</td>
<td>Atomic Write Color MSAA Sparse</td>
<td>Atomic Write Color MSAA Sparse</td>
<td>Atomic Write Color MSAA Sparse</td>
<td>Atomic Write Color MSAA Sparse</td>
<td>Atomic Write Color MSAA</td>
</tr>
<tr>
<td>R32Float 2,6</td>
<td>Write Color MSAA Blend</td>
<td>Write Color MSAA Blend Sparse</td>
<td>Write Color MSAA Blend</td>
<td>Write Color MSAA Blend</td>
<td>Write Color MSAA Blend</td>
<td>Write Color MSAA Blend</td>
<td>Write Color MSAA Blend Sparse</td>
<td>Write Color MSAA Blend Sparse</td>
<td>Write Color MSAA Blend Sparse</td>
<td>All</td>
<td>All</td>
<td>All</td>
</tr>
<tr>
<td>RG16Unorm RG16Snorm</td>
<td>All</td>
<td>All</td>
<td>Filter Write Color MSAA Blend</td>
<td>Filter Write Color MSAA Blend</td>
<td>All</td>
<td>All</td>
<td>All</td>
<td>All</td>
<td>All</td>
<td>All</td>
<td>All</td>
<td>All</td>
</tr>
<tr>
<td>RG16Uint RG16Sint</td>
<td>Write Color MSAA</td>
<td>Write Color MSAA Sparse</td>
<td>Write Color MSAA</td>
<td>Write Color MSAA</td>
<td>Write Color MSAA</td>
<td>Write Color MSAA</td>
<td>Write Color MSAA Sparse</td>
<td>Write Color MSAA Sparse</td>
<td>Write Color MSAA Sparse</td>
<td>Write Color MSAA Sparse</td>
<td>Write Color MSAA Sparse</td>
<td>Write Color MSAA</td>
</tr>
<tr>
<td>RG16Float</td>
<td>All</td>
<td>All</td>
<td>All</td>
<td>All</td>
<td>All</td>
<td>All</td>
<td>All</td>
<td>All</td>
<td>All</td>
<td>All</td>
<td>All</td>
<td>All</td>
</tr>
<tr>
<td>RGBA8Unorm 2</td>
<td>All</td>
<td>All</td>
<td>All</td>
<td>All</td>
<td>All</td>
<td>All</td>
<td>All</td>
<td>All</td>
<td>All</td>
<td>All</td>
<td>All</td>
<td>All</td>
</tr>
<tr>
<td>RGBA8Unorm_sRGB</td>
<td>Filter Color MSAA Resolve Blend</td>
<td>All</td>
<td>All</td>
<td>All</td>
<td>All</td>
<td>All</td>
<td>All</td>
<td>All</td>
<td>All</td>
<td>All</td>
<td>All</td>
<td>Filter Color MSAA Resolve Blend</td>
</tr>
<tr>
<td>RGBA8Snorm</td>
<td>All</td>
<td>All</td>
<td>All</td>
<td>All</td>
<td>All</td>
<td>All</td>
<td>All</td>
<td>All</td>
<td>All</td>
<td>All</td>
<td>All</td>
<td>All</td>
</tr>
</table>

<a id="page-11"></a>

<table>
<tr>
<th>GPU family 1</th>
<th>Metal3</th>
<th>Metal4</th>
<th>Apple2</th>
<th>Apple3</th>
<th>Apple4</th>
<th>Apple5</th>
<th>Apple6</th>
<th>Apple7</th>
<th>Apple8</th>
<th>Apple9</th>
<th>Apple10</th>
<th>Mac2</th>
</tr>
<tr>
<td>RGBA8Uint 2 RGBA8Sint 2</td>
<td>Write Color MSAA</td>
<td>Write Color MSAA Sparse</td>
<td>Write Color MSAA</td>
<td>Write Color MSAA</td>
<td>Write Color MSAA</td>
<td>Write Color MSAA</td>
<td>Write Color MSAA Sparse</td>
<td>Write Color MSAA Sparse</td>
<td>Write Color MSAA Sparse</td>
<td>Write Color MSAA Sparse</td>
<td>Write Color MSAA Sparse</td>
<td>Write Color MSAA</td>
</tr>
<tr>
<td>BGRA8Unorm</td>
<td>All</td>
<td>All</td>
<td>All</td>
<td>All</td>
<td>All</td>
<td>All</td>
<td>All</td>
<td>All</td>
<td>All</td>
<td>All</td>
<td>All</td>
<td>All</td>
</tr>
<tr>
<td>BGRA8Unorm_sRGB</td>
<td>Filter Color MSAA Resolve Blend</td>
<td>All</td>
<td>All</td>
<td>All</td>
<td>All</td>
<td>All</td>
<td>All</td>
<td>All</td>
<td>All</td>
<td>All</td>
<td>All</td>
<td>Filter Color MSAA Resolve Blend</td>
</tr>
<tr>
<td>Packed 32-bit pixel formats</td>
<td colspan="12">Texture capabilities for packed 32-bit pixel formats by GPU family</td>
</tr>
<tr>
<td>RGB10A2Unorm</td>
<td>All</td>
<td>All</td>
<td>Filter Color MSAA Resolve Blend</td>
<td>All</td>
<td>All</td>
<td>All</td>
<td>All</td>
<td>All</td>
<td>All</td>
<td>All</td>
<td>All</td>
<td>All</td>
</tr>
<tr>
<td>BGR10A2Unorm</td>
<td>All</td>
<td>All</td>
<td>All</td>
<td>All</td>
<td>All</td>
<td>All</td>
<td>All</td>
<td>All</td>
<td>All</td>
<td>All</td>
<td>All</td>
<td>All</td>
</tr>
<tr>
<td>RGB10A2Uint</td>
<td>Write Color MSAA</td>
<td>Write Color MSAA Sparse</td>
<td>Color MSAA</td>
<td>Write Color MSAA</td>
<td>Write Color MSAA</td>
<td>Write Color MSAA</td>
<td>Write Color MSAA Sparse</td>
<td>Write Color MSAA Sparse</td>
<td>Write Color MSAA Sparse</td>
<td>Write Color MSAA Sparse</td>
<td>Write Color MSAA Sparse</td>
<td>Write Color MSAA</td>
</tr>
<tr>
<td>RG11B10Float 4</td>
<td>All</td>
<td>All</td>
<td>Filter Color MSAA Resolve Blend</td>
<td>All</td>
<td>All</td>
<td>All</td>
<td>All</td>
<td>All</td>
<td>All</td>
<td>All</td>
<td>All</td>
<td>All</td>
</tr>
<tr>
<td>RGB9E5Float 4</td>
<td>Filter</td>
<td>All</td>
<td>Filter Color MSAA Resolve Blend</td>
<td>All</td>
<td>All</td>
<td>All</td>
<td>All</td>
<td>All</td>
<td>All</td>
<td>All</td>
<td>All</td>
<td>Filter</td>
</tr>
<tr>
<td>Ordinary 64-bit pixel formats</td>
<td colspan="12">Texture capabilities for ordinary 64-bit pixel formats by GPU family</td>
</tr>
<tr>
<td>RG32Uint 7 RG32Sint</td>
<td>Write Color MSAA</td>
<td>Write Color MSAA Sparse</td>
<td>Write Color</td>
<td>Write Color</td>
<td>Write Color</td>
<td>Write Color</td>
<td>Write Color Sparse</td>
<td>Write Color MSAA Sparse</td>
<td>Atomic Write Color MSAA Sparse</td>
<td>Atomic Write Color MSAA Sparse</td>
<td>Atomic Write Color MSAA Sparse</td>
<td>Write Color MSAA</td>
</tr>
<tr>
<td>RG32Float 6</td>
<td>Write Color MSAA Blend</td>
<td>Write Color MSAA Blend Sparse</td>
<td>Write Color Blend</td>
<td>Write Color Blend</td>
<td>Write Color Blend</td>
<td>Write Color Blend</td>
<td>Write Color Blend Sparse</td>
<td>Write Color MSAA Blend Sparse</td>
<td>Write Color MSAA Blend Sparse</td>
<td>All</td>
<td>All</td>
<td>All</td>
</tr>
</table>

<a id="page-12"></a>

<table>
<tr>
<th>GPU family 1</th>
<th>Metal3</th>
<th>Metal4</th>
<th>Apple2</th>
<th>Apple3</th>
<th>Apple4</th>
<th>Apple5</th>
<th>Apple6</th>
<th>Apple7</th>
<th>Apple8</th>
<th>Apple9</th>
<th>Apple10</th>
<th>Mac2</th>
</tr>
<tr>
<td>RGBA16Unorm RGBA16Snorm</td>
<td>All</td>
<td>All</td>
<td>Filter Write Color MSAA Blend</td>
<td>Filter Write Color MSAA Blend</td>
<td>All</td>
<td>All</td>
<td>All</td>
<td>All</td>
<td>All</td>
<td>All</td>
<td>All</td>
<td>All</td>
</tr>
<tr>
<td>RGBA16Uint 2 RGBA16Sint 2</td>
<td>Write Color MSAA</td>
<td>Write Color MSAA Sparse</td>
<td>Write Color MSAA</td>
<td>Write Color MSAA</td>
<td>Write Color MSAA</td>
<td>Write Color MSAA</td>
<td>Write Color MSAA Sparse</td>
<td>Write Color MSAA Sparse</td>
<td>Write Color MSAA Sparse</td>
<td>Write Color MSAA Sparse</td>
<td>Write Color MSAA Sparse</td>
<td>Write Color MSAA</td>
</tr>
<tr>
<td>RGBA16Float 2</td>
<td>All</td>
<td>All</td>
<td>All</td>
<td>All</td>
<td>All</td>
<td>All</td>
<td>All</td>
<td>All</td>
<td>All</td>
<td>All</td>
<td>All</td>
<td>All</td>
</tr>
<tr>
<td>Ordinary 128-bit pixel formats</td>
<td colspan="12">Texture capabilities for ordinary 128-bit pixel formats by GPU family</td>
</tr>
<tr>
<td>RGBA32Uint 2 RGBA32Sint 2</td>
<td>Write Color MSAA</td>
<td>Write Color MSAA Sparse</td>
<td>Write Color</td>
<td>Write Color</td>
<td>Write Color</td>
<td>Write Color</td>
<td>Write Color Sparse</td>
<td>Write Color MSAA Sparse</td>
<td>Write Color MSAA Sparse</td>
<td>Write Color MSAA Sparse</td>
<td>Write Color MSAA Sparse</td>
<td>Write Color MSAA</td>
</tr>
<tr>
<td>RGBA32Float 2,6</td>
<td>Write Color MSAA Blend</td>
<td>Write Color MSAA Blend Sparse</td>
<td>Write Color Blend</td>
<td>Write Color Blend</td>
<td>Write Color Blend</td>
<td>Write Color Blend</td>
<td>Write Color Blend Sparse</td>
<td>Write Color MSAA Blend Sparse</td>
<td>Write Color MSAA Blend Sparse</td>
<td>All</td>
<td>All</td>
<td>All</td>
</tr>
<tr>
<td>Compressed pixel formats 4</td>
<td colspan="12">Texture capabilities for compressed pixel formats by GPU family</td>
</tr>
<tr>
<td>PVRTC pixel formats 8</td>
<td>Not available</td>
<td>Filter Sparse</td>
<td>Filter</td>
<td>Filter</td>
<td>Filter</td>
<td>Filter</td>
<td>Filter Sparse</td>
<td>Filter Sparse</td>
<td>Filter Sparse</td>
<td>Filter Sparse</td>
<td>Filter Sparse</td>
<td>Not available</td>
</tr>
<tr>
<td>EAC/ETC pixel formats</td>
<td>Not available</td>
<td>Filter Sparse</td>
<td>Filter</td>
<td>Filter</td>
<td>Filter</td>
<td>Filter</td>
<td>Filter Sparse</td>
<td>Filter Sparse</td>
<td>Filter Sparse</td>
<td>Filter Sparse</td>
<td>Filter Sparse</td>
<td>Not available</td>
</tr>
<tr>
<td>ASTC pixel formats</td>
<td>Not available</td>
<td>Filter Sparse</td>
<td>Filter</td>
<td>Filter</td>
<td>Filter</td>
<td>Filter</td>
<td>Filter Sparse</td>
<td>Filter Sparse</td>
<td>Filter Sparse</td>
<td>Filter Sparse</td>
<td>Filter Sparse</td>
<td>Not available</td>
</tr>
<tr>
<td>HDR ASTC pixel formats</td>
<td>Not available</td>
<td>Filter Sparse</td>
<td>Not available</td>
<td>Not available</td>
<td>Not available</td>
<td>Not available</td>
<td>Filter Sparse</td>
<td>Filter Sparse</td>
<td>Filter Sparse</td>
<td>Filter Sparse</td>
<td>Filter Sparse</td>
<td>Not available</td>
</tr>
<tr>
<td>BC pixel formats</td>
<td>Varies 9</td>
<td>Varies 9</td>
<td>Not available</td>
<td>Not available</td>
<td>Not available</td>
<td>Not available</td>
<td>Not available</td>
<td>Varies 9</td>
<td>Varies 9</td>
<td>Filter Sparse</td>
<td>Filter Sparse</td>
<td>Filter</td>
</tr>
<tr>
<td>YUV pixel formats 4</td>
<td colspan="12">Texture capabilities for YUV pixel formats by GPU family</td>
</tr>
<tr>
<td>GBGR422 BGRG422</td>
<td>Filter</td>
<td>Filter</td>
<td>Filter</td>
<td>Filter</td>
<td>Filter</td>
<td>Filter</td>
<td>Filter</td>
<td>Filter</td>
<td>Filter</td>
<td>Filter</td>
<td>Filter</td>
<td>Filter</td>
</tr>
<tr>
<td>Depth and stencil pixel formats 4</td>
<td colspan="12">Texture capabilities for depth and stencil pixel formats by GPU family</td>
</tr>
<tr>
<td>Depth16Unorm</td>
<td>Filter MSAA Resolve</td>
<td>Filter MSAA Resolve Sparse 10</td>
<td>Filter MSAA</td>
<td>Filter MSAA Resolve</td>
<td>Filter MSAA Resolve</td>
<td>Filter MSAA Resolve</td>
<td>Filter MSAA Resolve</td>
<td>Filter MSAA Resolve Sparse 10</td>
<td>Filter MSAA Resolve Sparse</td>
<td>Filter MSAA Resolve Sparse</td>
<td>Filter MSAA Resolve Sparse</td>
<td>Filter MSAA Resolve</td>
</tr>
<tr>
<td>Depth32Float 6</td>
<td>MSAA Resolve</td>
<td>MSAA Resolve Sparse 10</td>
<td>MSAA</td>
<td>MSAA Resolve</td>
<td>MSAA Resolve</td>
<td>MSAA Resolve</td>
<td>MSAA Resolve</td>
<td>MSAA Resolve Sparse 10</td>
<td>MSAA Resolve Sparse</td>
<td>Filter MSAA Resolve Sparse</td>
<td>Filter MSAA Resolve Sparse</td>
<td>Filter MSAA Resolve</td>
</tr>
</table>

<a id="page-13"></a>

<table>
<tr>
<th>GPU family 1</th>
<th>Metal3</th>
<th>Metal4</th>
<th>Apple2</th>
<th>Apple3</th>
<th>Apple4</th>
<th>Apple5</th>
<th>Apple6</th>
<th>Apple7</th>
<th>Apple8</th>
<th>Apple9</th>
<th>Apple10</th>
<th>Mac2</th>
</tr>
<tr>
<td>Stencil8</td>
<td>Not available</td>
<td>MSAA Resolve Sparse 10</td>
<td>MSAA</td>
<td>MSAA Resolve</td>
<td>MSAA Resolve</td>
<td>MSAA Resolve</td>
<td>MSAA Resolve</td>
<td>MSAA Resolve Sparse 10</td>
<td>MSAA Resolve Sparse</td>
<td>MSAA Resolve Sparse</td>
<td>MSAA Resolve Sparse</td>
<td>Not available</td>
</tr>
<tr>
<td>Depth24Unorm_Stencil8 11</td>
<td>Not available</td>
<td>Not available</td>
<td>Not available</td>
<td>Not available</td>
<td>Not available</td>
<td>Not available</td>
<td>Not available</td>
<td>Not available</td>
<td>Not available</td>
<td>Not available</td>
<td>Not available</td>
<td>Filter MSAA Resolve</td>
</tr>
<tr>
<td>Depth32Float_Stencil8</td>
<td>MSAA Resolve</td>
<td>MSAA Resolve</td>
<td>MSAA</td>
<td>MSAA Resolve</td>
<td>MSAA Resolve</td>
<td>MSAA Resolve</td>
<td>MSAA Resolve</td>
<td>MSAA Resolve</td>
<td>MSAA Resolve</td>
<td>Filter MSAA Resolve</td>
<td>Filter MSAA Resolve</td>
<td>Filter MSAA Resolve</td>
</tr>
<tr>
<td>X24_Stencil8</td>
<td>Not available</td>
<td>Not available</td>
<td>Not available</td>
<td>Not available</td>
<td>Not available</td>
<td>Not available</td>
<td>Not available</td>
<td>Not available</td>
<td>Not available</td>
<td>Not available</td>
<td>Not available</td>
<td>MSAA</td>
</tr>
<tr>
<td>X32_Stencil8</td>
<td>MSAA</td>
<td>MSAA</td>
<td>MSAA</td>
<td>MSAA</td>
<td>MSAA</td>
<td>MSAA</td>
<td>MSAA</td>
<td>MSAA</td>
<td>MSAA</td>
<td>MSAA</td>
<td>MSAA</td>
<td>MSAA</td>
</tr>
<tr>
<td>Extended-range and wide-color pixel formats</td>
<td colspan="12">Texture capabilities for extended-range and wide-color formats by GPU family</td>
</tr>
<tr>
<td>BGRA10_XRBGRA10_XR_sRGBBGR10_XRBGR10_XR_sRGB</td>
<td>Not available</td>
<td>All</td>
<td>Not available</td>
<td>All</td>
<td>All</td>
<td>All</td>
<td>All</td>
<td>All</td>
<td>All</td>
<td>All</td>
<td>All</td>
<td>Not available</td>
</tr>
</table>

1. See [MTLGPUFamily](<https://developer.apple.com/documentation/metal/mtlgpufamily>) for each GPU family’s enumeration constant.

2. Some GPUs support read/write textures where a kernel can both read from and write to a texture. You can check an individual GPU’s support for this feature by inspecting its MTLDevice.readWriteTextureSupport property at runtime.

3. The [A8Unorm](<https://developer.apple.com/documentation/metal/mtlpixelformat/a8unorm>) pixel format is incompatible with imageblocks with explicit layout. Use either an [R8Unorm](<https://developer.apple.com/documentation/metal/mtlpixelformat/r8unorm>) texture view, or imageblocks with implicit layout.

4. Formats in this group aren’t compatible with lossy texture compression through MTLTextureDescriptor.compressionType.

5. Textures with the [A1BGR5Unorm](<https://developer.apple.com/documentation/metal/mtlpixelformat/a1bgr5unorm>) or [ABGR4Unorm](<https://developer.apple.com/documentation/metal/mtlpixelformat/abgr4unorm>) format are incompatible with samplers using the [opaqueBlack](<https://developer.apple.com/documentation/metal/mtlsamplerbordercolor/opaqueblack>) border color.

6. Some GPUs in the Apple7, and Apple8 families additionally support the Filter and Resolve texture capabilities for 32-bit floating-point pixel formats in iPadOS. You can check an individual GPU’s support for this feature by inspecting the MTLDevice.supports32BitFloatFiltering property at runtime.

7. You can only apply the [RG32Uint](<https://developer.apple.com/documentation/metal/mtlpixelformat/rg32uint>) format to a ulong texture on a GPU that supports the 64-bit atomics feature.

8. Only the GPUs in [Apple3](<https://developer.apple.com/documentation/metal/mtlgpufamily/apple3>) and [Apple4](<https://developer.apple.com/documentation/metal/mtlgpufamily/apple4>) families support MTLSamplerAddressMode.clampToZero for the PVRTC pixel formats.

9. Some GPU devices in the [Apple7](<https://developer.apple.com/documentation/metal/mtlgpufamily/apple7>) and [Apple8](<https://developer.apple.com/documentation/metal/mtlgpufamily/apple8>) families support filtering and sparse BC-compressed textures in iPadOS. You can check an individual GPU’s support for this feature by inspecting its MTLDevice.supportsBCTextureCompression property at runtime. All Apple7 and Apple8 MacOS devices have support.

10. Some GPUs in the Apple7 family in iPadOS, as well as all GPUs in the Apple7 family in macOS, support Sparse depth and stencil textures with placement heap backing. You can check an individual GPU’s support for this feature by inspecting its  MTLDevice.supportsPlacementSparse property at runtime.

11. Some GPUs support MTLPixelFormat.depth24Unorm\_stencil8. You can check an individual GPU’s support for this feature by inspecting its MTLDevice.isDepth24Stencil8PixelFormatSupported property at runtime.

<a id="page-14"></a>

### **Texture buffer pixel formats**

These tables list the pixel formats that texture buffers support, and the GPU’s read/write access to textures with those formats: • All: The GPU can use the following accesses for a texture buffer with the pixel format: • Read: The GPU can use read access for a texture buffer with the pixel format. • Write: The GPU can use write access for a texture buffer with the pixel format. • Read/write: The GPU can use read\_write access for a texture buffer with the pixel format. 1

Note The GPU capabilities are generally the same across all hardware families, but some GPUs have additional options. 2

<table>
<tr>
<th colspan="2">Ordinary 8-bit pixel formats</th>
</tr>
<tr>
<td>Format</td>
<td>Access</td>
</tr>
<tr>
<td>A8Unorm</td>
<td>All</td>
</tr>
<tr>
<td>R8Unorm</td>
<td>All</td>
</tr>
<tr>
<td>R8Snorm</td>
<td>Read Write</td>
</tr>
<tr>
<td>R8Uint R8Sint</td>
<td>All</td>
</tr>
</table>

<table>
<tr>
<th colspan="2">Ordinary 32-bit pixel formats</th>
</tr>
<tr>
<td>Format</td>
<td>Access</td>
</tr>
<tr>
<td>R32Uint R32Sint</td>
<td>All 3</td>
</tr>
<tr>
<td>R32Float</td>
<td>All</td>
</tr>
<tr>
<td>RG16Unorm RG16Snorm</td>
<td>Read Write</td>
</tr>
<tr>
<td>RG16Uint RG16Sint</td>
<td>Read Write</td>
</tr>
<tr>
<td>RG16Float</td>
<td>Read Write</td>
</tr>
<tr>
<td>RGBA8Unorm</td>
<td>All</td>
</tr>
<tr>
<td>RGBA8Snorm</td>
<td>Read Write</td>
</tr>
<tr>
<td>RGBA8Uint RGBA8Sint</td>
<td>All</td>
</tr>
<tr>
<td>BGRA8Unorm</td>
<td>Read</td>
</tr>
</table>

<table>
<tr>
<th colspan="2">Packed 32-bit pixel formats</th>
</tr>
<tr>
<td>Format</td>
<td>Access</td>
</tr>
<tr>
<td>RGB10A2Unorm</td>
<td>Read Write</td>
</tr>
<tr>
<td>RGB10A2Uint</td>
<td>Read Write</td>
</tr>
<tr>
<td>RG11B10Float</td>
<td>Read Write</td>
</tr>
</table>

<table>
<tr>
<th colspan="2">Ordinary 64-bit pixel formats</th>
</tr>
<tr>
<td>Format</td>
<td>Access</td>
</tr>
<tr>
<td>RG32Uint RG32Sint</td>
<td>Read Write</td>
</tr>
<tr>
<td>RG32Float</td>
<td>Read Write</td>
</tr>
<tr>
<td>RGBA16Unorm RGBA16Snorm</td>
<td>Read Write</td>
</tr>
<tr>
<td>RGBA16Uint RGBA16Sint</td>
<td>All</td>
</tr>
<tr>
<td>RGBA16Float</td>
<td>All</td>
</tr>
</table>

<table>
<tr>
<th colspan="2">Ordinary 16-bit pixel formats</th>
</tr>
<tr>
<td>Format</td>
<td>Access</td>
</tr>
<tr>
<td>R16Unorm R16Snorm</td>
<td>Read Write</td>
</tr>
<tr>
<td>R16Uint R16Sint</td>
<td>All</td>
</tr>
<tr>
<td>R16Float</td>
<td>All</td>
</tr>
<tr>
<td>RG8Unorm</td>
<td>Read Write</td>
</tr>
<tr>
<td>RG8Snorm</td>
<td>Read Write</td>
</tr>
<tr>
<td>RG8Uint RG8Sint</td>
<td>Read Write</td>
</tr>
</table>

<table>
<tr>
<th colspan="2">Ordinary 128-bit pixel formats</th>
</tr>
<tr>
<td>Format</td>
<td>Access</td>
</tr>
<tr>
<td>RGBA32Uint RGBA32Sint</td>
<td>All</td>
</tr>
<tr>
<td>RGBA32Float</td>
<td>All</td>
</tr>
</table>

1. GPUs with the Tier 2 feature set support read\_write access to textures. You can check an individual GPU’s support for this feature by inspecting its MTLDevice.readWriteTextureSupport property at runtime.

2. Some devices support this pixel format. Check a device by inspecting its MTLDevice.depth24Stencil8PixelFormatSupported property at runtime.

3. GPUs that support texture atomics (see feature availability by GPU family) also support atomics in read/write texture buffers with this pixel format.

<a id="page-15"></a>

 Apple Inc. Copyright © 2014-2026 Apple Inc. All rights reserved.

No part of this publication may be reproduced, stored in a retrieval system, or transmitted, in any form or by any means, mechanical, electronic, photocopying, recording, or otherwise, without prior written permission of Apple Inc., with the following exceptions: Any person is hereby authorized to store documentation on a single computer or device for personal use only and to print copies of documentation for personal use provided that the documentation contains Apple’s copyright notice.

No licenses, express or implied, are granted with respect to any of the technology described in this document. Apple retains all intellectual property rights associated with the technology described in this document. This document is intended to assist application developers to develop applications only for Apple-branded products.

Apple Inc. One Apple Park Way Cupertino, CA 95014

Apple is a trademark of Apple Inc., registered in the U.S. and other countries.

APPLE MAKES NO WARRANTY OR REPRESENTATION, EITHER EXPRESS OR IMPLIED, WITH RESPECT TO THIS DOCUMENT, ITS QUALITY, ACCURACY, MERCHANTABILITY, OR FITNESS FOR A PARTICULAR PURPOSE. AS A RESULT, THIS DOCUMENT IS PROVIDED “AS IS,” AND YOU, THE READER, ARE ASSUMING THE ENTIRE RISK AS TO ITS QUALITY AND ACCURACY.

IN NO EVENT WILL APPLE BE LIABLE FOR DIRECT, INDIRECT, SPECIAL, INCIDENTAL, OR CONSEQUENTIAL DAMAGES RESULTING FROM ANY DEFECT, ERROR OR INACCURACY IN THIS DOCUMENT, even if advised of the possibility of such damages.

Some jurisdictions do not allow the exclusion of implied warranties or liability, so the above exclusion may not apply to you.
