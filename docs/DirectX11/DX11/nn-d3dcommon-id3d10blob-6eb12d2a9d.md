Source: [https://learn.microsoft.com/en-us/windows/win32/api/d3dcommon/nn-d3dcommon-id3d10blob](<https://learn.microsoft.com/en-us/windows/win32/api/d3dcommon/nn-d3dcommon-id3d10blob>)

# ID3D10Blob interface


## -description

This interface is used to return arbitrary-length data.

## -inheritance

The <b>ID3D10Blob</b> interface inherits from the <a href="/windows/desktop/api/unknwn/nn-unknwn-iunknown">IUnknown</a> interface. <b>ID3D10Blob</b> also has these types of members:

## -remarks

The <a href="/previous-versions/windows/desktop/legacy/ff728743(v=vs.85)">ID3DBlob</a> interface is type-defined in the D3DCommon.h header file as a <b>ID3D10Blob</b> interface, which is fully defined in the D3DCommon.h header file.
          <b>ID3DBlob</b> is version-neutral and can be used in code for any Direct3D version.
        

Blobs can be used as a data buffer, storing vertex, adjacency, and material information during mesh optimization and loading operations.
          Also, these objects are used to return object code and error messages in APIs that compile vertex, geometry and pixel shaders.

## -see-also

<a href="/windows/desktop/direct3d11/d3d11-graphics-reference-d3d11-common-interfaces">Common Version Interfaces</a>



<a href="/previous-versions/windows/desktop/legacy/ff728743(v=vs.85)">ID3DBlob</a>



<a href="/windows/desktop/api/unknwn/nn-unknwn-iunknown">IUnknown</a>