Source: [https://learn.microsoft.com/en-us/windows/win32/api/d3dcommon/nn-d3dcommon-id3dinclude](<https://learn.microsoft.com/en-us/windows/win32/api/d3dcommon/nn-d3dcommon-id3dinclude>)

# ID3DInclude interface


## -description

<b>ID3DInclude</b> is an include interface that the user implements to allow an application to call user-overridable methods for opening and closing shader #include files.

## -inheritance

The <b>ID3DInclude</b> interface inherits from the <a href="/windows/desktop/api/unknwn/nn-unknwn-iunknown">IUnknown</a> interface. <b>ID3DInclude</b> also has these types of members:
<ul>
<li><a href="/">Methods</a></li>
</ul>

## -remarks

To use this interface, create an interface that inherits from <b>ID3DInclude</b> and implement custom behavior for the methods.

## -see-also

<a href="/windows/desktop/direct3d11/d3d11-graphics-reference-d3d11-common-interfaces">Common Version Interfaces</a>