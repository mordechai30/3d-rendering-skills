Source: [https://learn.microsoft.com/en-us/windows/win32/api/d3d11/ns-d3d11-cd3d11_rect](<https://learn.microsoft.com/en-us/windows/win32/api/d3d11/ns-d3d11-cd3d11_rect>)

# CD3D11_RECT structure


## -description

Represents a rectangle and provides convenience methods for creating rectangles.

## -struct-fields

## -remarks

Here is how D3D11.h defines <b>CD3D11_RECT</b>:


<div class="code"><span><table>
<tr>
<th></th>
</tr>
<tr>
<td>
<pre>struct CD3D11_RECT : public D3D11_RECT
{
    CD3D11_RECT()
    {}
    explicit CD3D11_RECT( const D3D11_RECT&amp; o ) :
        D3D11_RECT( o )
    {}
    explicit CD3D11_RECT(
        LONG Left,
        LONG Top,
        LONG Right,
        LONG Bottom )
    {
        left = Left;
        top = Top;
        right = Right;
        bottom = Bottom;
    }
    ~CD3D11_RECT() {}
    operator const D3D11_RECT&amp;() const { return *this; }
};
</pre>
</td>
</tr>
</table></span></div>

## -see-also

<a href="/windows/desktop/direct3d11/cd3d11-helper-classes">CD3D11 Helper Structures</a>