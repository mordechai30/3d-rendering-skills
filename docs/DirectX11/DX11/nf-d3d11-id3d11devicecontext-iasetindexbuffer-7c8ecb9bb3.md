Source: [https://learn.microsoft.com/en-us/windows/win32/api/D3D11/nf-d3d11-id3d11devicecontext-iasetindexbuffer](<https://learn.microsoft.com/en-us/windows/win32/api/D3D11/nf-d3d11-id3d11devicecontext-iasetindexbuffer>)

# ID3D11DeviceContext::IASetIndexBuffer


## -description

Bind an index buffer to the input-assembler stage.

## -parameters

### -param pIndexBuffer [in, optional]

Type: <b><a href="/windows/desktop/api/d3d11/nn-d3d11-id3d11buffer">ID3D11Buffer</a>*</b>

A pointer to an <a href="/windows/desktop/api/d3d11/nn-d3d11-id3d11buffer">ID3D11Buffer</a> object, that contains indices. The index buffer must have been created with
            the <a href="/windows/desktop/api/d3d11/ne-d3d11-d3d11_bind_flag">D3D11_BIND_INDEX_BUFFER</a> flag.

### -param Format [in]

Type: <b><a href="/windows/desktop/api/dxgiformat/ne-dxgiformat-dxgi_format">DXGI_FORMAT</a></b>

A <a href="/windows/desktop/api/dxgiformat/ne-dxgiformat-dxgi_format">DXGI_FORMAT</a> that specifies the format of the data in the index buffer. The only formats allowed for index
            buffer data are 16-bit (DXGI_FORMAT_R16_UINT) and 32-bit (DXGI_FORMAT_R32_UINT) integers.

### -param Offset [in]

Type: <b><a href="/windows/desktop/WinProg/windows-data-types">UINT</a></b>

Offset (in bytes) from the start of the index buffer to the first index to use.

## -remarks

For information about creating index buffers, see <a href="/windows/desktop/direct3d11/overviews-direct3d-11-resources-buffers-index-how-to">How to: Create an Index Buffer</a>.
        

Calling this method using a buffer that is currently bound for writing (i.e. bound to the stream output pipeline stage) will effectively bind
          <b>NULL</b> instead because a buffer cannot be bound as both an input and an output at the same time.
        

The debug layer will generate a warning whenever a resource is prevented from being bound simultaneously as an input and an output, but this will
          not prevent invalid data from being used by the runtime.
        

The method will hold a reference to the interfaces passed in.
          This differs from the device state behavior in Direct3D 10.
        

<b>Windows Phone 8:
        </b> This API is supported.

## -see-also

<a href="/windows/desktop/api/d3d11/nn-d3d11-id3d11devicecontext">ID3D11DeviceContext</a>