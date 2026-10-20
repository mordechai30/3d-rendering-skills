Source: [https://learn.microsoft.com/en-us/windows/win32/api/d3dcommon/nf-d3dcommon-id3ddestructionotifier-unregisterdestructioncallback](<https://learn.microsoft.com/en-us/windows/win32/api/d3dcommon/nf-d3dcommon-id3ddestructionotifier-unregisterdestructioncallback>)

## -description

Unregisters a callback that was registered with [RegisterDestructionCallback](./nf-d3dcommon-id3ddestructionotifier-registerdestructioncallback-ecc2ab1848.md).

## -parameters

### -param callbackID

Type: **[UINT](/windows/win32/winprog/windows-data-types)**

The **UINT** that was created by the *pCallbackID* argument to <b><a href="/windows/win32/api/d3dcommon/nf-d3dcommon-id3ddestructionotifier-registerdestructioncallback">ID3DDestructionNotifier::RegisterDestructionCallback</a></b>.

## -returns

Type: **[HRESULT](/windows/win32/com/structure-of-com-error-codes)**

If this function succeeds, it returns **S_OK**.

## -see-also

<a href="/windows/win32/api/d3dcommon/nn-d3dcommon-id3ddestructionotifier">ID3DDestructionNotifier</a>

<a href="/windows/win32/api/d3dcommon/nf-d3dcommon-id3ddestructionotifier-registerdestructioncallback">ID3DDestructionNotifier::RegisterDestructionCallback</a>