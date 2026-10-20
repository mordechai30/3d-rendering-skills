Source: [https://learn.microsoft.com/en-us/windows/win32/api/d3d11/ns-d3d11-cd3d11_buffer_desc](<https://learn.microsoft.com/en-us/windows/win32/api/d3d11/ns-d3d11-cd3d11_buffer_desc>)

# CD3D11_BUFFER_DESC structure


## -description

Represents a buffer and provides convenience methods for creating buffers.

## -struct-fields

### -field CD3D11_BUFFER_DESC

TBD

### -field ~CD3D11_BUFFER_DESC

TBD

### -field operator const D3D11_BUFFER_DESC&

TBD

### -field D3D11_BUFFER_DESC

 




##### - See Below.

## -remarks

Here is how D3D11.h defines <b>CD3D11_BUFFER_DESC</b>:


```

struct CD3D11_BUFFER_DESC : public D3D11_BUFFER_DESC
{
    CD3D11_BUFFER_DESC()
    {}
    explicit CD3D11_BUFFER_DESC( const D3D11_BUFFER_DESC& o ) :
        D3D11_BUFFER_DESC( o )
    {}
    explicit CD3D11_BUFFER_DESC(
        UINT byteWidth,
        UINT bindFlags,
        D3D11_USAGE usage = D3D11_USAGE_DEFAULT,
        UINT cpuaccessFlags = 0,
        UINT miscFlags = 0,
        UINT structureByteStride = 0 )
    {
        ByteWidth = byteWidth;
        Usage = usage;
        BindFlags = bindFlags;
        CPUAccessFlags = cpuaccessFlags ;
        MiscFlags = miscFlags;
        StructureByteStride = structureByteStride;
    }
    ~CD3D11_BUFFER_DESC() {}
    operator const D3D11_BUFFER_DESC&() const { return *this; }
};

```

## -see-also

<a href="/windows/desktop/direct3d11/cd3d11-helper-classes">CD3D11 Helper Structures</a>