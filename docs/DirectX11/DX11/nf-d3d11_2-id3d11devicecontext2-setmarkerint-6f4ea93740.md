Source: [https://learn.microsoft.com/en-us/windows/win32/api/d3d11_2/nf-d3d11_2-id3d11devicecontext2-setmarkerint](<https://learn.microsoft.com/en-us/windows/win32/api/d3d11_2/nf-d3d11_2-id3d11devicecontext2-setmarkerint>)

# ID3D11DeviceContext2::SetMarkerInt


## -description

Allows applications to annotate graphics commands.

## -parameters

### -param pLabel [in]

An optional string that will be logged to <a href="/previous-versions/dotnet/netframework-3.0/ms751538(v=vs.85)">ETW</a> when ETW logging is active. If <b>‘#d’</b> appears in the string, it will be replaced by the value of the <i>Data</i> parameter similar to the way <b>printf</b> works.

### -param Data

A signed data value that will be logged to ETW when ETW logging is active.

## -remarks

<b>SetMarkerInt</b> allows applications to annotate graphics commands, in order to provide more context to what the GPU is executing. When ETW logging or a support tool is enabled, an additional marker is correlated between the CPU and GPU timelines. The <i>pLabel</i> and <i>Data</i> value are logged to ETW. When the appropriate ETW logging is not enabled, this method does nothing.

## -see-also

<a href="/windows/desktop/api/d3d11_2/nn-d3d11_2-id3d11devicecontext2">ID3D11DeviceContext2</a>