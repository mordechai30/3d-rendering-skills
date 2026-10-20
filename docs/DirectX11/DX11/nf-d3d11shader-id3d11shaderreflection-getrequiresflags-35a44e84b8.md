Source: [https://learn.microsoft.com/en-us/windows/win32/api/D3D11Shader/nf-d3d11shader-id3d11shaderreflection-getrequiresflags](<https://learn.microsoft.com/en-us/windows/win32/api/D3D11Shader/nf-d3d11shader-id3d11shaderreflection-getrequiresflags>)

# ID3D11ShaderReflection::GetRequiresFlags


## -description

Gets a group of flags that indicates the requirements of a shader.



## -returns

Type: <b>UINT64</b>

A value that contains a combination of one or more shader requirements flags; each flag specifies a requirement of the shader. A default value of 0 means there are no requirements. 

<table>
<tr>
<th>Shader requirement flag</th>
<th>Description</th>
</tr>
<tr>
<td><b>D3D_SHADER_REQUIRES_DOUBLES</b></td>
<td>Shader requires that the graphics driver and hardware support double data type. For more info, see <a href="/windows/desktop/api/d3d11/ns-d3d11-d3d11_feature_data_doubles">D3D11_FEATURE_DATA_DOUBLES</a>.</td>
</tr>
<tr>
<td><b>D3D_SHADER_REQUIRES_EARLY_DEPTH_STENCIL</b></td>
<td>Shader requires an early depth stencil.</td>
</tr>
<tr>
<td><b>D3D_SHADER_REQUIRES_UAVS_AT_EVERY_STAGE</b></td>
<td>Shader requires unordered access views (UAVs) at every pipeline stage.</td>
</tr>
<tr>
<td><b>D3D_SHADER_REQUIRES_64_UAVS</b></td>
<td>Shader requires 64 UAVs.</td>
</tr>
<tr>
<td><b>D3D_SHADER_REQUIRES_MINIMUM_PRECISION</b></td>
<td>Shader requires the graphics driver and hardware to support minimum precision. For more info, see <a href="/windows/desktop/direct3dhlsl/using-hlsl-minimum-precision">Using HLSL minimum precision</a>.</td>
</tr>
<tr>
<td><b>D3D_SHADER_REQUIRES_11_1_DOUBLE_EXTENSIONS</b></td>
<td>Shader requires that the graphics driver and hardware support extended doubles instructions. For more info, see the <b>ExtendedDoublesShaderInstructions</b> member of <a href="/windows/desktop/api/d3d11/ns-d3d11-d3d11_feature_data_d3d11_options">D3D11_FEATURE_DATA_D3D11_OPTIONS</a>.</td>
</tr>
<tr>
<td><b>D3D_SHADER_REQUIRES_11_1_SHADER_EXTENSIONS</b></td>
<td>Shader requires that the graphics driver and hardware support the <a href="/windows/desktop/direct3dhlsl/dx-graphics-hlsl-msad4">msad4</a> intrinsic function in shaders. For more info, see the <b>SAD4ShaderInstructions</b> member of <a href="/windows/desktop/api/d3d11/ns-d3d11-d3d11_feature_data_d3d11_options">D3D11_FEATURE_DATA_D3D11_OPTIONS</a>.</td>
</tr>
<tr>
<td><b>D3D_SHADER_REQUIRES_LEVEL_9_COMPARISON_FILTERING</b></td>
<td>Shader requires that the graphics driver and hardware support Direct3D 9 shadow support. For more info, see <a href="/windows/desktop/api/d3d11/ns-d3d11-d3d11_feature_data_d3d9_shadow_support">D3D11_FEATURE_DATA_D3D9_SHADOW_SUPPORT</a>.</td>
</tr>
<tr>
<td><b>D3D_SHADER_REQUIRES_TILED_RESOURCES</b></td>
<td>Shader requires that the graphics driver and hardware support tiled resources. For more info, see <a href="/windows/desktop/api/d3d11_2/nf-d3d11_2-id3d11device2-getresourcetiling">GetResourceTiling</a>. </td>
</tr>
</table>

## -remarks

Here is how the D3D11Shader.h header defines the shader requirements flags:


```cpp

#define D3D_SHADER_REQUIRES_DOUBLES                         0x00000001
#define D3D_SHADER_REQUIRES_EARLY_DEPTH_STENCIL             0x00000002
#define D3D_SHADER_REQUIRES_UAVS_AT_EVERY_STAGE             0x00000004
#define D3D_SHADER_REQUIRES_64_UAVS                         0x00000008
#define D3D_SHADER_REQUIRES_MINIMUM_PRECISION               0x00000010
#define D3D_SHADER_REQUIRES_11_1_DOUBLE_EXTENSIONS          0x00000020
#define D3D_SHADER_REQUIRES_11_1_SHADER_EXTENSIONS          0x00000040
#define D3D_SHADER_REQUIRES_LEVEL_9_COMPARISON_FILTERING    0x00000080

```

## -see-also

<a href="/windows/desktop/api/d3d11shader/nn-d3d11shader-id3d11shaderreflection">ID3D11ShaderReflection</a>