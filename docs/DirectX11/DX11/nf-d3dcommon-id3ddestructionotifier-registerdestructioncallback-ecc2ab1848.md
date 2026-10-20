Source: [https://learn.microsoft.com/en-us/windows/win32/api/d3dcommon/nf-d3dcommon-id3ddestructionotifier-registerdestructioncallback](<https://learn.microsoft.com/en-us/windows/win32/api/d3dcommon/nf-d3dcommon-id3ddestructionotifier-registerdestructioncallback>)

## -description

Registers a user-defined callback to be invoked on destruction of the object from which this [ID3DDestructionNotifier](./nn-d3dcommon-id3ddestructionotifier-ec4bb8a679.md) was created.

## -parameters

### -param callbackFn

Type: <b>PFN_DESTRUCTION_CALLBACK</b>

A user-defined callback to be invoked when the object is destroyed.

### -param pData

Type: **void\***

The data to pass to *callbackFn* when invoked

### -param pCallbackID

Type: **[UINT](/windows/win32/winprog/windows-data-types)\***

Pointer to a **UINT** used to identify the callback, and to pass to <a href="/windows/win32/api/d3dcommon/nf-d3dcommon-id3ddestructionotifier-unregisterdestructioncallback"></a> to unregister the callback.

## -returns

Type: **[HRESULT](/windows/win32/com/structure-of-com-error-codes)**

If this function succeeds, it returns **S_OK**.

## -remarks

An example of this interface being used to log the destruction of an **ID3D12Resource**.

```cppcx
#include <d3dcommon.h> // for ID3DDestructionNotifier

ComPtr<ID3D12Resource> resource = ...;

ComPtr<ID3DDestructionNotifier> notifier;
if (SUCCEEDED(resource.As(&notifier)))
{
    UINT callbackId;
    ThrowIfFailed(notifier->RegisterDestructionCallback(LogResourceReleased, nullptr, &callbackId));
}

void LogResourceReleased(void* context)
{
    OutputDebugString("Resource released!\n");
}
```

## -see-also

<a href="/windows/win32/api/d3dcommon/nn-d3dcommon-id3ddestructionotifier">ID3DDestructionNotifier</a>

<a href="/windows/win32/api/d3dcommon/nf-d3dcommon-id3ddestructionotifier-unregisterdestructioncallback">ID3DDestructionNotifier::UnregisterDestructionCallback</a>