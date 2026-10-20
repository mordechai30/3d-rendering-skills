Source: [https://learn.microsoft.com/en-us/windows/win32/api/D3D11/nf-d3d11-id3d11device-createhullshader](<https://learn.microsoft.com/en-us/windows/win32/api/D3D11/nf-d3d11-id3d11device-createhullshader>)

# ID3D11Device::CreateHullShader


## -description

Create a <a href="/windows/desktop/direct3d11/direct3d-11-advanced-stages-tessellation">hull shader</a>.

## -parameters

### -param pShaderBytecode [in]

Type: <b>const void*</b>

A pointer to a compiled shader.

### -param BytecodeLength [in]

Type: <b><a href="/windows/desktop/WinProg/windows-data-types">SIZE_T</a></b>

Size of the compiled shader.

### -param pClassLinkage [in, optional]

Type: <b><a href="/windows/desktop/api/d3d11/nn-d3d11-id3d11classlinkage">ID3D11ClassLinkage</a>*</b>

A pointer to a class linkage interface (see <a href="/windows/desktop/api/d3d11/nn-d3d11-id3d11classlinkage">ID3D11ClassLinkage</a>); the value can be <b>NULL</b>.

### -param ppHullShader [out, optional]

Type: <b><a href="/windows/desktop/api/d3d11/nn-d3d11-id3d11hullshader">ID3D11HullShader</a>**</b>

Address of a pointer to a <a href="/windows/desktop/api/d3d11/nn-d3d11-id3d11hullshader">ID3D11HullShader</a> interface.

## -returns

Type: <b><a href="/windows/win32/com/structure-of-com-error-codes">HRESULT</a></b>

This method returns one of the <a href="/windows/desktop/direct3d11/d3d11-graphics-reference-returnvalues">Direct3D 11 Return Codes</a>.

## -remarks

The Direct3D 11.1 runtime, which is available starting with Windows 8, provides the following new functionality for <b>CreateHullShader</b>.

The following shader model 5.0 instructions are available to just pixel shaders and compute shaders in the Direct3D 11.0 runtime. For the Direct3D 11.1 runtime, because unordered access views (UAV) are available at all shader stages, you can use these instructions in all shader stages.

Therefore, if you use the following shader model 5.0 instructions in a hull shader, you can successfully pass the compiled hull shader to <i>pShaderBytecode</i>. That is, the call to <b>CreateHullShader</b> succeeds.

If you pass a compiled shader to <i>pShaderBytecode</i> that uses any of the following instructions on a device that doesn’t support UAVs at every shader stage (including existing drivers that are not implemented to support UAVs at every shader stage), <b>CreateHullShader</b> fails.  <b>CreateHullShader</b> also fails if the shader tries to use a UAV slot beyond the set of UAV slots that the hardware supports.

<ul>
<li>
<a href="/windows/desktop/direct3dhlsl/dcl-uav-typed--sm5---asm-">dcl_uav_typed</a>
</li>
<li>
<a href="/windows/desktop/direct3dhlsl/dcl-uav-raw--sm5---asm-">dcl_uav_raw</a>
</li>
<li>
<a href="/windows/desktop/direct3dhlsl/dcl-uav-structured--sm5---asm-">dcl_uav_structured</a>
</li>
<li>
<a href="/windows/desktop/direct3dhlsl/ld-raw--sm5---asm-">ld_raw</a>
</li>
<li>
<a href="/windows/desktop/direct3dhlsl/ld-structured--sm5---asm-">ld_structured</a>
</li>
<li>
<a href="/windows/desktop/direct3dhlsl/ld-uav-typed--sm5---asm-">ld_uav_typed</a>
</li>
<li>
<a href="/windows/desktop/direct3dhlsl/store-raw--sm5---asm-">store_raw</a>
</li>
<li>
<a href="/windows/desktop/direct3dhlsl/store-structured--sm5---asm-">store_structured</a>
</li>
<li>
<a href="/windows/desktop/direct3dhlsl/store-uav-typed--sm5---asm-">store_uav_typed</a>
</li>
<li>
<a href="/windows/desktop/direct3dhlsl/sync--sm5---asm-">sync_uglobal</a>
</li>
<li>All atomics and immediate atomics (for example, <a href="/windows/desktop/direct3dhlsl/atomic-and--sm5---asm-">atomic_and</a> and <a href="/windows/desktop/direct3dhlsl/imm-atomic-and--sm5---asm-">imm_atomic_and</a>)</li>
</ul>

## -see-also

<a href="/windows/desktop/api/d3d11/nn-d3d11-id3d11device">ID3D11Device</a>