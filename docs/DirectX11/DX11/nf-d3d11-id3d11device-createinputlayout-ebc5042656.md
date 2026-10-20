Source: [https://learn.microsoft.com/en-us/windows/win32/api/D3D11/nf-d3d11-id3d11device-createinputlayout](<https://learn.microsoft.com/en-us/windows/win32/api/D3D11/nf-d3d11-id3d11device-createinputlayout>)

# ID3D11Device::CreateInputLayout


## -description

Create an input-layout object to describe the input-buffer data for the input-assembler stage.

## -parameters

### -param pInputElementDescs [in]

Type: <b>const <a href="/windows/desktop/api/d3d11/ns-d3d11-d3d11_input_element_desc">D3D11_INPUT_ELEMENT_DESC</a>*</b>

An array of the input-assembler stage input data types; each type is described by an element description (see <a href="/windows/desktop/api/d3d11/ns-d3d11-d3d11_input_element_desc">D3D11_INPUT_ELEMENT_DESC</a>).

### -param NumElements [in]

Type: <b><a href="/windows/desktop/WinProg/windows-data-types">UINT</a></b>

The number of input-data types in the array of input-elements.

### -param pShaderBytecodeWithInputSignature [in]

Type: <b>const void*</b>

A pointer to the compiled shader.  The compiled shader code contains a input signature which is validated against the array of elements. See remarks.

### -param BytecodeLength [in]

Type: <b><a href="/windows/desktop/WinProg/windows-data-types">SIZE_T</a></b>

Size of the compiled shader.

### -param ppInputLayout [out, optional]

Type: <b><a href="/windows/desktop/api/d3d11/nn-d3d11-id3d11inputlayout">ID3D11InputLayout</a>**</b>

A pointer to the input-layout object created (see <a href="/windows/desktop/api/d3d11/nn-d3d11-id3d11inputlayout">ID3D11InputLayout</a>). To validate the other input parameters, set this pointer to be <b>NULL</b> and verify that the method returns S_FALSE.

## -returns

Type: <b><a href="/windows/win32/com/structure-of-com-error-codes">HRESULT</a></b>

If the method succeeds, the return code is S_OK. See <a href="/windows/desktop/direct3d11/d3d11-graphics-reference-returnvalues">Direct3D 11 Return Codes</a> for failing error codes.

## -remarks

After creating an input layout object, it must be bound to the input-assembler stage before calling a draw API.

Once an input-layout object is created from a shader signature, the input-layout object can be reused with any other shader that has an identical input signature (semantics included). This can simplify the creation of input-layout objects when you are working with many shaders with identical inputs.

If a data type in the input-layout declaration does not match the data type in a shader-input signature, CreateInputLayout will generate a warning during compilation. The warning is simply to call attention to the fact that the data may be reinterpreted when read from a register. You may either disregard this warning (if reinterpretation is intentional) or make the data types match in both declarations to eliminate the warning.
        

<b>Windows Phone 8:
        </b> This API is supported.

## -see-also

<a href="/windows/desktop/api/d3d11/nn-d3d11-id3d11device">ID3D11Device</a>