Source: [https://learn.microsoft.com/en-us/windows/win32/api/D3D11Shader/nf-d3d11shader-id3d11shaderreflection-getthreadgroupsize](<https://learn.microsoft.com/en-us/windows/win32/api/D3D11Shader/nf-d3d11shader-id3d11shaderreflection-getthreadgroupsize>)

# ID3D11ShaderReflection::GetThreadGroupSize


## -description

Retrieves the sizes, in units of threads, of the X, Y, and Z dimensions of the shader's thread-group grid.

## -parameters

### -param pSizeX [out, optional]

Type: <b><a href="/windows/desktop/WinProg/windows-data-types">UINT</a>*</b>

A pointer to the size, in threads, of the x-dimension of the thread-group grid. The maximum size is 1024.

### -param pSizeY [out, optional]

Type: <b><a href="/windows/desktop/WinProg/windows-data-types">UINT</a>*</b>

A pointer to the size, in threads, of the y-dimension of the thread-group grid. The maximum size is 1024.

### -param pSizeZ [out, optional]

Type: <b><a href="/windows/desktop/WinProg/windows-data-types">UINT</a>*</b>

A pointer to the size, in threads, of the z-dimension of the thread-group grid. The maximum size is 64.

## -returns

Type: <b><a href="/windows/desktop/WinProg/windows-data-types">UINT</a></b>

Returns the total size, in threads, of the thread-group grid by calculating the product of the size of each dimension.



``` syntax
*pSizeX * *pSizeY * *pSizeZ;
```


## -remarks

This method's interface is hosted in the out-of-box DLL D3DCompiler_xx.dll.
      

When a compute shader is written it defines the actions of a single thread group only. If multiple thread groups are required, it is the role of the <a href="/windows/desktop/api/d3d11/nf-d3d11-id3d11devicecontext-dispatch">ID3D11DeviceContext::Dispatch</a> call to issue multiple thread groups.

## -see-also

<a href="/windows/desktop/api/d3d11shader/nn-d3d11shader-id3d11shaderreflection">ID3D11ShaderReflection</a>