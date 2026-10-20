Source: [https://learn.microsoft.com/en-us/windows/win32/api/D3D11/ns-d3d11-cd3d11_blend_desc](<https://learn.microsoft.com/en-us/windows/win32/api/D3D11/ns-d3d11-cd3d11_blend_desc>)

# CD3D11_BLEND_DESC structure


## -description

Represents a blend-state structure and provides convenience methods for creating blend-state structures.

## -struct-fields

### -field CD3D11_BLEND_DESC

TBD

### -field ~CD3D11_BLEND_DESC

TBD

### -field operator const D3D11_BLEND_DESC&

TBD

### -field D3D11_BLEND_DESC

 




##### - See Below.

## -remarks

Here is how D3D11.h defines <b>CD3D11_BLEND_DESC</b>:


```

struct CD3D11_BLEND_DESC : public D3D11_BLEND_DESC
{
    CD3D11_BLEND_DESC()
    {}
    explicit CD3D11_BLEND_DESC( const D3D11_BLEND_DESC& o ) :
        D3D11_BLEND_DESC( o )
    {}
    explicit CD3D11_BLEND_DESC( CD3D11_DEFAULT )
    {
        AlphaToCoverageEnable = FALSE;
        IndependentBlendEnable = FALSE;
        const D3D11_RENDER_TARGET_BLEND_DESC defaultRenderTargetBlendDesc =
        {
            FALSE,
            D3D11_BLEND_ONE, D3D11_BLEND_ZERO, D3D11_BLEND_OP_ADD,
            D3D11_BLEND_ONE, D3D11_BLEND_ZERO, D3D11_BLEND_OP_ADD,
            D3D11_COLOR_WRITE_ENABLE_ALL,
        };
        for (UINT i = 0; i < D3D11_SIMULTANEOUS_RENDER_TARGET_COUNT; ++i)
            RenderTarget[ i ] = defaultRenderTargetBlendDesc;
    }
    ~CD3D11_BLEND_DESC() {}
    operator const D3D11_BLEND_DESC&() const { return *this; }
};

```

## -see-also

<a href="/windows/desktop/direct3d11/cd3d11-helper-classes">CD3D11 Helper Structures</a>