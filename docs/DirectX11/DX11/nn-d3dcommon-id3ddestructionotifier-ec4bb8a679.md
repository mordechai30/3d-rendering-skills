Source: [https://learn.microsoft.com/en-us/windows/win32/api/d3dcommon/nn-d3dcommon-id3ddestructionotifier](<https://learn.microsoft.com/en-us/windows/win32/api/d3dcommon/nn-d3dcommon-id3ddestructionotifier>)

## -description

**ID3DDestructionNotifier** is an interface that you can use to register for callbacks when a Direct3D nano-COM object is destroyed.

To acquire an instance of this interface, call <a href="/windows/win32/api/unknwn/nf-unknwn-iunknown-queryinterface(refiid_void)"></a> on a Direct3D object with the **IID** of **ID3DDestructionNotifier**.

Using <b>ID3DDestructionNotifier</b> instead of <b><a href="/windows/win32/api/d3d12/nf-d3d12-id3d12object-setprivatedatainterface">ID3D12Object::SetPrivateDataInterface</a></b> or Direct3D 11 equivalents provides
stronger guarantees about the order of destruction. With <b>ID3DDestructionNotifier</b>, implicit relationships&mdash;such as an <b><a href="/windows/win32/api/d3d11/nn-d3d11-id3d11view">ID3D11View</a></b> holding a reference to its underlying <b><a href="/windows/win32/api/d3d11/nn-d3d11-id3d11resource">ID3D11Resource</a></b>&mdash;are guaranteed to be valid and for the referenced object (here, the **ID3D11Object**) to still be alive when the destruction callback is invoked. With <b><a href="/windows/win32/api/d3d12/nf-d3d12-id3d12object-setprivatedatainterface">ID3D12Object::SetPrivateDataInterface</a></b>, the implicit references can be released before the destruction callback is invoked.

It isn't safe to access the object being destructed during the callback.

## -inheritance

The **ID3DDestructionNotifier** interface inherits from the <a href="/windows/win32/api/unknwn/nn-unknwn-iunknown">IUnknown</a> interface. 

## -remarks

The <b>ID3DDestructionNotifier</b> can be used to track resources which are being unexpectedly released early, or providing a log of object disposal.

## -see-also

<a href="/windows/win32/api/d3dcommon/nf-d3dcommon-id3ddestructionotifier-registerdestructioncallback">ID3DDestructionNotifier::RegisterDestructionCallback</a>

<a href="/windows/win32/api/d3dcommon/nf-d3dcommon-id3ddestructionotifier-unregisterdestructioncallback">ID3DDestructionNotifier::UnregisterDestructionCallback</a>

<a href="/windows/desktop/direct3d11/d3d11-graphics-reference-d3d11-common-interfaces">Common Version Interfaces</a>