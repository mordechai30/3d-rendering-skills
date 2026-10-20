Source: [https://learn.microsoft.com/en-us/windows/win32/direct3d11/d3d10-graphics-programming-guide-input-assembler-stage](<https://learn.microsoft.com/en-us/windows/win32/direct3d11/d3d10-graphics-programming-guide-input-assembler-stage>)

# Input-Assembler Stage

The Direct3D 10 and higher API separates functional areas of the pipeline into stages; the first stage in the pipeline is the input-assembler (IA) stage.

The purpose of the input-assembler stage is to read primitive data (points, lines and/or triangles) from user-filled buffers and assemble the data into primitives that will be used by the other pipeline stages. The IA stage can assemble vertices into several different [primitive types](./d3d10-graphics-programming-guide-primitive-topologies-bcfd143d42.md) (such as line lists, triangle strips, or primitives with adjacency). New primitive types (such as a line list with adjacency or a triangle list with adjacency) have been added to support the geometry shader.

Adjacency information is visible to an application only in a geometry shader. If a geometry shader were invoked with a triangle including adjacency, for instance, the input data would contain 3 vertices for each triangle and 3 vertices for adjacency data per triangle.

When the input-assembler stage is requested to output adjacency data, the input data must include adjacency data. This may require providing a dummy vertex (forming a degenerate triangle), or perhaps by flagging in one of the vertex attributes whether the vertex exists or not. This would also need to be detected and handled by a geometry shader, although culling of degenerate geometry will happen in the rasterizer stage.

While assembling primitives, a secondary purpose of the IA is to attach [system-generated values](/windows/desktop/direct3dhlsl/dx-graphics-hlsl-semantics) to help make shaders more efficient. System-generated values are text strings that are also called semantics. All three shader stages are constructed from a common shader core, and the shader core uses system-generated values (such as a primitive id, an instance id, or a vertex id) so that a shader stage can reduce processing to only those primitives, instances, or vertices that have not already been processed.

As shown in the [pipeline-block diagram](/windows/desktop/direct3d10/d3d10-graphics-programming-guide-pipeline-stages), once the IA stage reads data from memory (assembles the data into primitives and attaches system-generated values), the data is output to the [vertex shader stage](/previous-versions//bb205146(v=vs.85)).


## In this section



| Topic                                                                                                                                   | Description                                                                                                                                                                                                                                                                                                                       |
|-----------------------------------------------------------------------------------------------------------------------------------------|-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| [Getting Started with the Input-Assembler Stage](./d3d10-graphics-programming-guide-input-assembler-stage-getting-started-41dee2d9f1.md)<br/> | There are a few steps necessary to initialize the input-assembler (IA) stage. For example, you need to create buffer resources with the vertex data that the pipeline needs, tell the IA stage where the buffers are and what type of data they contain, and specify the type of primitives to assemble from the data.<br/> |
| [Primitive Topologies](./d3d10-graphics-programming-guide-primitive-topologies-bcfd143d42.md)<br/>                                            | Direct3D 10 and higher supports several primitive types (or topologies) that are represented by the [**D3D\_PRIMITIVE\_TOPOLOGY**](./ne-d3dcommon-d3d_primitive_topology-b4ddcd7505.md) enumerated type. These types define how vertices are interpreted and rendered by the pipeline.<br/>                                                          |
| [Using the Input-Assembler Stage without Buffers](./d3d10-graphics-programming-guide-input-assembler-stage-no-buffers-ebd16a0e84.md)<br/>     | Creating and binding buffers is not necessary if your shaders don't require buffers. This section contains an example of simple vertex and pixel shaders that draw a single triangle.<br/>                                                                                                                                  |
| [Using System-Generated Values](./d3d10-graphics-programming-guide-input-assembler-stage-using-312fc616f3.md)<br/>                            | System-generated values are generated by the IA stage (based on user-supplied input [semantics](/windows/desktop/direct3dhlsl/dx-graphics-hlsl-semantics)) to allow certain efficiencies in shader operations. <br/>                                                                                                                         |



 

## Related topics

<dl> <dt>

[Graphics Pipeline](./overviews-direct3d-11-graphics-pipeline-afe69eb859.md)
</dt> <dt>

[Pipeline Stages (Direct3D 10)](/windows/desktop/direct3d10/d3d10-graphics-programming-guide-pipeline-stages)
</dt> </dl>