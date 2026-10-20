Source: [https://learn.microsoft.com/en-us/windows/win32/api/D3D11/nf-d3d11-id3d11device-checkcounter](<https://learn.microsoft.com/en-us/windows/win32/api/D3D11/nf-d3d11-id3d11device-checkcounter>)

# ID3D11Device::CheckCounter


## -description

Get the type, name, units of measure, and a description of an existing counter.

## -parameters

### -param pDesc [in]

Type: <b>const <a href="/windows/desktop/api/d3d11/ns-d3d11-d3d11_counter_desc">D3D11_COUNTER_DESC</a>*</b>

Pointer to a counter description (see <a href="/windows/desktop/api/d3d11/ns-d3d11-d3d11_counter_desc">D3D11_COUNTER_DESC</a>). Specifies which counter information is to be retrieved about.

### -param pType [out]

Type: <b><a href="/windows/desktop/api/d3d11/ne-d3d11-d3d11_counter_type">D3D11_COUNTER_TYPE</a>*</b>

Pointer to the data type of a counter (see <a href="/windows/desktop/api/d3d11/ne-d3d11-d3d11_counter_type">D3D11_COUNTER_TYPE</a>). Specifies the data type of the counter being retrieved.

### -param pActiveCounters [out]

Type: <b><a href="/windows/desktop/WinProg/windows-data-types">UINT</a>*</b>

Pointer to the number of hardware counters that are needed for this counter type to be created. All instances of the same counter type use the same hardware counters.

### -param szName [out, optional]

Type: <b><a href="/windows/desktop/WinProg/windows-data-types">LPSTR</a></b>

String to be filled with a brief name for the counter. May be <b>NULL</b> if the application is not interested in the name of the counter.

### -param pNameLength [in, out, optional]

Type: <b><a href="/windows/desktop/WinProg/windows-data-types">UINT</a>*</b>

Length of the string returned to szName. Can be <b>NULL</b>.

### -param szUnits [out, optional]

Type: <b><a href="/windows/desktop/WinProg/windows-data-types">LPSTR</a></b>

Name of the units a counter measures, provided the memory the pointer points to has enough room to hold the string. Can be <b>NULL</b>. The returned string will always be in English.

### -param pUnitsLength [in, out, optional]

Type: <b><a href="/windows/desktop/WinProg/windows-data-types">UINT</a>*</b>

Length of the string returned to szUnits. Can be <b>NULL</b>.

### -param szDescription [out, optional]

Type: <b><a href="/windows/desktop/WinProg/windows-data-types">LPSTR</a></b>

A description of the counter, provided the memory the pointer points to has enough room to hold the string. Can be <b>NULL</b>. The returned string will always be in English.

### -param pDescriptionLength [in, out, optional]

Type: <b><a href="/windows/desktop/WinProg/windows-data-types">UINT</a>*</b>

Length of the string returned to szDescription. Can be <b>NULL</b>.

## -returns

Type: <b><a href="/windows/win32/com/structure-of-com-error-codes">HRESULT</a></b>

This method returns one of the following <a href="/windows/desktop/direct3d11/d3d11-graphics-reference-returnvalues">Direct3D 11 Return Codes</a>.

## -remarks

Length parameters can be <b>NULL</b>, which indicates the application is not interested in the length nor the corresponding string value. When a length parameter is non-<b>NULL</b> and the corresponding string is <b>NULL</b>, the input value of the length parameter is ignored, and the length of the corresponding string (including terminating <b>NULL</b>) will be returned through the length parameter. When length and the corresponding parameter are both non-<b>NULL</b>, the input value of length is checked to ensure there is enough room, and then the length of the string (including terminating <b>NULL</b> character) is passed out through the length parameter.
        

<b>Windows Phone 8:
        </b> This API is supported.

## -see-also

<a href="/windows/desktop/api/d3d11/nn-d3d11-id3d11device">ID3D11Device</a>