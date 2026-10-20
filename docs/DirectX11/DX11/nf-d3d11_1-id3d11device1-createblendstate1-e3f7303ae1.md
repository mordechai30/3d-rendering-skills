Source: [https://learn.microsoft.com/en-us/windows/win32/api/D3D11_1/nf-d3d11_1-id3d11device1-createblendstate1](<https://learn.microsoft.com/en-us/windows/win32/api/D3D11_1/nf-d3d11_1-id3d11device1-createblendstate1>)

# ID3D11Device1::CreateBlendState1


## -description

Creates a blend-state object that encapsulates blend state for the <a href="/windows/desktop/direct3d11/d3d10-graphics-programming-guide-output-merger-stage">output-merger stage</a> and allows the configuration of logic operations.

## -parameters

### -param pBlendStateDesc [in]

A pointer to a  <a href="/windows/win32/api/d3d11_1/ns-d3d11_1-d3d11_blend_desc1">D3D11_BLEND_DESC1</a> structure that describes blend state.

### -param ppBlendState [out, optional]

Address of a pointer to the <a href="/windows/desktop/api/d3d11_1/nn-d3d11_1-id3d11blendstate1">ID3D11BlendState1</a> interface for the blend-state object created.

## -returns

This method returns E_OUTOFMEMORY if there is insufficient memory to create the blend-state object.  
        See <a href="/windows/desktop/direct3d11/d3d11-graphics-reference-returnvalues">Direct3D 11 Return Codes</a> for other possible return values.

## -remarks

The logical operations (those that enable bitwise logical operations between pixel shader output and render target contents, refer to <a href="/windows/desktop/api/d3d11_1/ns-d3d11_1-d3d11_render_target_blend_desc1">D3D11_RENDER_TARGET_BLEND_DESC1</a> ) are only available on certain feature levels; call <a href="/windows/desktop/api/d3d11/nf-d3d11-id3d11device-checkfeaturesupport">CheckFeatureSupport</a> with D3D11_FEATURE_D3D11_OPTIONS set, to ensure support by checking the boolean field  <i>OutputMergerLogicOp</i> of <a href="/windows/desktop/api/d3d11/ns-d3d11-d3d11_feature_data_d3d11_options">D3D11_FEATURE_DATA_D3D11_OPTIONS</a>.

An app can create up to 4096 unique blend-state objects. For each object created, the runtime checks to see if a previous object 
      has the same state. If such a previous object exists, the runtime will return a pointer to previous instance instead of creating a duplicate object.

## -see-also

<a href="/windows/desktop/api/d3d11_1/nn-d3d11_1-id3d11device1">ID3D11Device1</a>