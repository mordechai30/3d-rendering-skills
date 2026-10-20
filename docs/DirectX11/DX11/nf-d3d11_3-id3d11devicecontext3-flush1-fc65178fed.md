Source: [https://learn.microsoft.com/en-us/windows/win32/api/d3d11_3/nf-d3d11_3-id3d11devicecontext3-flush1](<https://learn.microsoft.com/en-us/windows/win32/api/d3d11_3/nf-d3d11_3-id3d11devicecontext3-flush1>)

# ID3D11DeviceContext3::Flush1


## -description

Sends queued-up commands in the command buffer to the graphics processing unit (GPU), with a specified context type and an optional event handle to create an event query.

## -parameters

### -param ContextType

Type: <b><a href="/windows/desktop/api/d3d11_3/ne-d3d11_3-d3d11_context_type">D3D11_CONTEXT_TYPE</a></b>

A <a href="/windows/desktop/api/d3d11_3/ne-d3d11_3-d3d11_context_type">D3D11_CONTEXT_TYPE</a> that specifies the context in which a query occurs, such as a 3D command queue, 3D compute queue, 3D copy queue, video, or image.

### -param hEvent [in, optional]

Type: <b>HANDLE</b>

An optional event handle. When specified, this method creates an event query.
            

<b>Flush1</b> operates asynchronously, therefore it can return either before or after the GPU finishes executing the queued graphics commands, which will eventually complete.
              To create an event query, you can call <a href="/windows/desktop/api/d3d11/nf-d3d11-id3d11device-createquery">ID3D11Device::CreateQuery</a> with the
              value <a href="/windows/desktop/api/d3d11/ne-d3d11-d3d11_query">D3D11_QUERY_EVENT</a> value.
              To determine when the GPU is finished processing the graphics commands,
              you can then use that event query in a call to <a href="/windows/desktop/api/d3d11/nf-d3d11-id3d11devicecontext-getdata">ID3D11DeviceContext::GetData</a>.

## -remarks

<b>Flush1</b> has parameters.
          For more information, see
          <a href="/windows/desktop/api/d3d11/nf-d3d11-id3d11devicecontext-flush">ID3D11DeviceContext::Flush</a>, which doesn't have parameters.

## -see-also

<a href="/windows/desktop/api/d3d11_3/nn-d3d11_3-id3d11devicecontext3">ID3D11DeviceContext3</a>



<a href="/windows/desktop/api/d3d11/nf-d3d11-id3d11devicecontext-flush">ID3D11DeviceContext::Flush</a>