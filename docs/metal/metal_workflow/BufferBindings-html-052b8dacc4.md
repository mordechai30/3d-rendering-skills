Source: [https://developer.apple.com/library/archive/documentation/3DDrawing/Conceptual/MTLBestPracticesGuide/BufferBindings.html](<https://developer.apple.com/library/archive/documentation/3DDrawing/Conceptual/MTLBestPracticesGuide/BufferBindings.html>)

<a id="//apple_ref/doc/uid/TP40016642-CH28"></a>

<a id="//apple_ref/doc/uid/TP40016642-CH28-SW3"></a>



<a id="buffer-bindings"></a>

## Buffer Bindings

**Best Practice:** Use an appropriate method to bind your buffer data to a graphics or compute function.

Metal provides several API options for binding buffer data to a graphics or compute function so it can be processed by the GPU.

<a id="//apple_ref/doc/uid/TP40016642-CH28-DontLinkElementID_27"></a>



Note

This chapter uses *vertex* function bindings as examples. Metal provides equivalent APIs for *fragment* and *kernel* functions in the `MTLRenderCommandEncoder` and `MTLComputeCommandEncoder` classes.

The `setVertexBytes:length:atIndex:` method is the best option for binding a very small amount (less than 4 KB) of dynamic buffer data to a vertex function, as shown in Listing 5-1. This method avoids the overhead of creating an intermediary `MTLBuffer` object. Instead, Metal manages a transient buffer for you.

<a id="//apple_ref/doc/uid/TP40016642-CH28-SW2"></a>

**Listing 5-1**Binding a very small amount (less than 4 KB) of dynamic buffer data

1. `float _verySmallData = 1.0;`
2. `[renderEncoder setVertexBytes:&_verySmallData length:sizeof(float) atIndex:0];`

If your data size is larger than 4 KB, create a `MTLBuffer` object once and update its contents as needed. Call the `setVertexBuffer:offset:atIndex:` method to bind the buffer to a vertex function; if your buffer contains data used in multiple draw calls, call the `setVertexBufferOffset:atIndex:` method afterward to update the buffer offset so it points to the location of the corresponding draw call data, as shown in Listing 5-2. You do not need to rebind the currently bound buffer if you are only updating its offset.

<a id="//apple_ref/doc/uid/TP40016642-CH28-SW1"></a>

**Listing 5-2**Updating the offset of a bound buffer

1. `// Bind the vertex buffer once`
2. `[renderEncoder setVertexBuffer:_vertexBuffer[_frameIndex] offset:0 atIndex:0];`
3. `for(int i=0; i<_drawCalls; i++)`
4. `{`
5. `// Update the vertex buffer offset for each draw call`
6. `[renderEncoder setVertexBufferOffset:i*_sizeOfVertices atIndex:0];`
8. `// Draw the vertices`
9. `[renderEncoder drawPrimitives:MTLPrimitiveTypeTriangle vertexStart:0 vertexCount:_vertexCount];`
10. `}`

<a id="next_previous"></a>

[Triple Buffering](./TripleBuffering-html-4fbf2e3432.md#//apple_ref/doc/uid/TP40016642-CH5-SW1)

[Drawables](./Drawables-html-a6bbc21e80.md#//apple_ref/doc/uid/TP40016642-CH2-SW1)

Copyright © 2018 Apple Inc. All rights reserved.
[Terms of Use](http://www.apple.com/legal/terms/site.html) |
[Privacy Policy](http://www.apple.com/privacy/) |
[Updated: 2017-03-27](https://developer.apple.com/library/archive/documentation/3DDrawing/Conceptual/MTLBestPracticesGuide/RevisionHistory.html#//apple_ref/doc/uid/TP40016642-CH99-DontLinkElementID_50)
