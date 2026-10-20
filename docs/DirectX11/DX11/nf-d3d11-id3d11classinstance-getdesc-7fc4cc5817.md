Source: [https://learn.microsoft.com/en-us/windows/win32/api/d3d11/nf-d3d11-id3d11classinstance-getdesc](<https://learn.microsoft.com/en-us/windows/win32/api/d3d11/nf-d3d11-id3d11classinstance-getdesc>)

# ID3D11ClassInstance::GetDesc


## -description

Gets a description of the current HLSL class.

## -parameters

### -param pDesc [out]

Type: <b><a href="/windows/desktop/api/d3d11/ns-d3d11-d3d11_class_instance_desc">D3D11_CLASS_INSTANCE_DESC</a>*</b>

A pointer to a <a href="/windows/desktop/api/d3d11/ns-d3d11-d3d11_class_instance_desc">D3D11_CLASS_INSTANCE_DESC</a> structure that describes the current HLSL class.

## -remarks

For more information about using the <a href="/windows/desktop/api/d3d11/nn-d3d11-id3d11classinstance">ID3D11ClassInstance</a> interface, see
          <a href="/windows/desktop/direct3dhlsl/overviews-direct3d-11-hlsl-dynamic-linking">Dynamic Linking</a>.
        

An instance is not restricted to being used for a single type in a single shader. An instance is flexible and can be used for any shader that used the same type name or instance name when the instance was generated.
        

<ul>
<li>A created instance will work for any shader that contains a type of the same type name.
            For instance, a class instance created with the type name <b>DefaultShader</b> would work in any shader that contained a type <b>DefaultShader</b> even though several shaders could describe a different type.
          </li>
<li>A gotten instance maps directly to an instance name/index in a shader.
            A class instance acquired using GetClassInstance will work for any shader that contains a class instance of the name used to generate the runtime instance, the instance does not have to be the same type in all of the shaders it's used in.
          </li>
</ul>
An instance does not replace the importance of reflection for a particular shader since a gotten instance will not know its slot location and a created instance only specifies a type name.
        

<b>Windows Phone 8:
        </b> This API is supported.

## -see-also

<a href="/windows/desktop/api/d3d11/nn-d3d11-id3d11classinstance">ID3D11ClassInstance</a>