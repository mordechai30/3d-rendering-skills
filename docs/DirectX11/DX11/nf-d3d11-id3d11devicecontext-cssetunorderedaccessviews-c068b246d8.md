Source: [https://learn.microsoft.com/en-us/windows/win32/api/D3D11/nf-d3d11-id3d11devicecontext-cssetunorderedaccessviews](<https://learn.microsoft.com/en-us/windows/win32/api/D3D11/nf-d3d11-id3d11devicecontext-cssetunorderedaccessviews>)

# ID3D11DeviceContext::CSSetUnorderedAccessViews


## -description

Sets an array of views for an unordered resource.

## -parameters

### -param StartSlot [in]

Type: <b><a href="/windows/desktop/WinProg/windows-data-types">UINT</a></b>

Index of the first element in the zero-based array to begin setting  (ranges from 0 to D3D11_1_UAV_SLOT_COUNT - 1). D3D11_1_UAV_SLOT_COUNT is defined as 64.

### -param NumUAVs [in]

Type: <b><a href="/windows/desktop/WinProg/windows-data-types">UINT</a></b>

Number of views to set (ranges from 0 to D3D11_1_UAV_SLOT_COUNT - <i>StartSlot</i>).

### -param ppUnorderedAccessViews [in, optional]

Type: <b><a href="/windows/desktop/api/d3d11/nn-d3d11-id3d11unorderedaccessview">ID3D11UnorderedAccessView</a>*</b>

A pointer to an array of <a href="/windows/desktop/api/d3d11/nn-d3d11-id3d11unorderedaccessview">ID3D11UnorderedAccessView</a> pointers to be set by the method.

### -param pUAVInitialCounts [in, optional]

Type: <b>const <a href="/windows/desktop/WinProg/windows-data-types">UINT</a>*</b>

An array of append and consume buffer offsets. A value of -1 indicates to keep the current offset. Any other values set the hidden counter
            for that appendable and consumable UAV. <i>pUAVInitialCounts</i> is only relevant for UAVs that were created with either
            <a href="/windows/desktop/api/d3d11/ne-d3d11-d3d11_buffer_uav_flag">D3D11_BUFFER_UAV_FLAG_APPEND</a> or <b>D3D11_BUFFER_UAV_FLAG_COUNTER</b> specified
            when the UAV was created; otherwise, the argument is ignored.

## -remarks

<b>Windows Phone 8:
        </b> This API is supported.

## -see-also

<a href="/windows/desktop/api/d3d11/nn-d3d11-id3d11devicecontext">ID3D11DeviceContext</a>