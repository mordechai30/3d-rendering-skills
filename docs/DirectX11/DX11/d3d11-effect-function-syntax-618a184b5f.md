Source: [https://learn.microsoft.com/en-us/windows/win32/direct3d11/d3d11-effect-function-syntax](<https://learn.microsoft.com/en-us/windows/win32/direct3d11/d3d11-effect-function-syntax>)

# Effect Function Syntax (Direct3D 11)

An effect function is written in HLSL and is declared with the syntax described in this section.

## Syntax

*ReturnType* *FunctionName* ( \[ *ArgumentList* \] )

{

<dl> \[ *Statements* \]  
</dl>

};



| Name         | Description                                                                                                                                                                                                                                                          |
|--------------|----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| ReturnType   | Any [HLSL type](/windows/desktop/direct3dhlsl/dx-graphics-hlsl-variable-syntax)                                                                                                                                                                                                       |
| FunctionName | An ASCII string that uniquely identifies the name of the shader function.                                                                                                                                                                                            |
| ArgumentList | One or more arguments, separated by commas (see [Function Arguments (DirectX HLSL)](/windows/desktop/direct3dhlsl/dx-graphics-hlsl-function-parameters)).                                                                                                                             |
| Statements   | One or more statements (see [Statements (DirectX HLSL)](/windows/desktop/direct3dhlsl/dx-graphics-hlsl-statements)) that make up the body of the function. If a function is defined without a body, it is considered to be a prototype; and must be redefined with a body before use. |



 

An effect function may be a shader or it may simply be a function called by a shader. A function is uniquely identified by its name, the types of its parameters, and the target platform; therefore, functions can be overloaded. Any valid HLSL function should fit this format; for a more detailed list of syntax for HLSL functions, see [Functions (DirectX HLSL)](/windows/desktop/direct3dhlsl/dx-graphics-hlsl-functions).

## Example

The following is an example of a pixel shader function.


```
       
PS_OUTPUT RenderScenePS( VS_OUTPUT In,
                         uniform bool bTexture ) 
{ 
    PS_OUTPUT Output;

    // Lookup mesh texture and modulate it with diffuse
    if( bTexture )
        Output.RGBColor = g_MeshTexture.Sample(MeshTextureSampler, In.TextureUV) *  
                              In.Diffuse;
    else
        Output.RGBColor = In.Diffuse;

    return Output;
}
```



## Related topics

<dl> <dt>

[Effect Format](./d3d11-effect-format-a65df79688.md)
</dt> </dl>