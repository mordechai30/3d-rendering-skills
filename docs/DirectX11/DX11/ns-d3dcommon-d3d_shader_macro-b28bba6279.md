Source: [https://learn.microsoft.com/en-us/windows/win32/api/d3dcommon/ns-d3dcommon-d3d_shader_macro](<https://learn.microsoft.com/en-us/windows/win32/api/d3dcommon/ns-d3dcommon-d3d_shader_macro>)

# D3D_SHADER_MACRO structure


## -description

Defines a shader macro.

## -struct-fields

### -field Name

The macro name.

### -field Definition

The macro definition.

## -remarks

You can use shader macros in your shaders. The <b>D3D_SHADER_MACRO</b> structure defines a single shader macro as shown in the following example:


```

D3D_SHADER_MACRO Shader_Macros[] = { "zero", "0", NULL, NULL };

```


The following shader or effect creation functions take an array of shader macros as an input parameter:

<ul>
<li>
<a href="/windows/desktop/api/d3d10shader/nf-d3d10shader-d3d10compileshader">D3D10CompileShader</a>
</li>
<li>
<a href="/windows/desktop/direct3d10/d3dx10createeffectfromfile">D3DX10CreateEffectFromFile</a>
</li>
<li>
<a href="/windows/desktop/direct3d10/d3dx10preprocessshaderfromfile">D3DX10PreprocessShaderFromFile</a>
</li>
<li>
<a href="/windows/desktop/direct3d11/d3dx11createasyncshaderpreprocessprocessor">D3DX11CreateAsyncShaderPreprocessProcessor</a>
</li>
</ul>

## -see-also

<a href="/windows/desktop/direct3d11/d3d11-graphics-reference-d3d11-common-structures">Common Version Structures</a>