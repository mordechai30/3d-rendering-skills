Source: [https://learn.microsoft.com/en-us/windows/win32/api/d3d11_2/nf-d3d11_2-id3d11devicecontext2-begineventint](<https://learn.microsoft.com/en-us/windows/win32/api/d3d11_2/nf-d3d11_2-id3d11devicecontext2-begineventint>)

# ID3D11DeviceContext2::BeginEventInt


## -description

Allows applications to annotate the beginning of a range of graphics commands.

## -parameters

### -param pLabel [in]

An optional string that will be logged to <a href="/previous-versions/dotnet/netframework-3.0/ms751538(v=vs.85)">ETW</a> when ETW logging is active. If <b>‘#d’</b> appears in the string, it will be replaced by the value of the <i>Data</i> parameter similar to the way <b>printf</b> works.

### -param Data

A signed data value that will be logged to ETW when ETW logging is active.

## -remarks

<b>BeginEventInt</b> allows applications to annotate the beginning of a range of graphics commands, in order to provide more context to what the GPU is executing. When <a href="/previous-versions/dotnet/netframework-3.0/ms751538(v=vs.85)">ETW</a> logging (or a supported tool) is enabled, an additional marker is correlated between the CPU and GPU timelines. The <i>pLabel</i> and <i>Data</i> value are logged to ETW. When the appropriate ETW logging is not enabled, this method does nothing.

## -see-also

<a href="/windows/desktop/api/d3d11_2/nn-d3d11_2-id3d11devicecontext2">ID3D11DeviceContext2</a>